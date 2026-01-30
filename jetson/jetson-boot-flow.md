# Jetson Boot Flow

Ref: https://docs.nvidia.com/jetson/archives/r36.3/DeveloperGuide/AR/BootArchitecture/JetsonOrinSeriesBootFlow.html

![[Bootflow.png]]

- The boot flow here is parallel and multi-processor:
	- BPMP boots its own firmware.
	- PSC boots its own firmware.
	- CPU boots linux via UEFI.
	- Security domains are strictly enforced.

## BPMP (Boot and Power Management Processor):

- The BPMP is responsible for the following
	- Boot time and system management.
	- Power management and clocking of main CPU.
	- Handles inter-process communication between OS (running on main CPU) and hardware components.
- The BPMP firmware can operate in different privileges:
	- **TZ**(Trust Zone):
		- In a trusted zone operating environment the BPMP has higher privileges and access to hardware registers.
		- Here the BPMP handles secureboot, encryption keys and security sensitive power management to ensure only trusted code can control system power states.
	- **NON-TZ**:
		- This refers to a runtime environment where BPMP firmware manages general power and clock tasks, such as scaling down GPU power to reduce battery or cool down the device without accessing secure or protected keys.
- The BootROM (BR) is the first code that runs after power-on.
- It is hardwired into SOC, and started executing as BPMP exists reset state.

### SoC BR (BootROM):

- BR typically runs on a smaller ARM7 core of a dedicated Processor.
- BR initializes the boot media and loads BR-BCT, PSCBL1, MB1, MB1BCT and then halts.

### Boot Media:

- Boot media is the storage device holding the bootloader, kernel and operation systems.
- Often times the internal EMMC is primary and mandatory for bootloader partitions MB1, BCT and the OS can boot from other OS sources.

### BR - BCT(BootROM - Boot Configuration Table):

- This is a crucial component used in secure boot process.
- This holds essential settings for boot process, memory initialisation and security configuration before the main bootloader (MB1/UEFI) takes over.
- The BR-BCT is authenticated by BootROM using Public Key Cryptography (PKC) stored in write-once-read-multiple fuses.
- Orin system typically uses multiple copies of BR-BCT for robustness.

### BPMP-FW(Boot and Power Management Processor - Firmware):

- This is a specialised firmware running on a dedicated cortex M processor.
- It manages the system power, clocks, resets and initiates low level hardware during bootime and runtime, independent of the main CPU and OS.

### PSCBL1 (Platform Security Contoller - Boot Loader Stage 1):

- This is a critical early stage secure boot component loaded by the BootROM, it initializes security operations, audits subsequent stages like MB1, and manages secure keys loading, making it essential for device integrity and rollback protection.

### PSCB-FW(Platform Security Controller - Firmware):

- This is also a critical part of the secure boot chain, functioning of as the firmware that run on the platform security controller hardware inside the SoC.
- PSCB-FW is responsible for managing security services during early boot process, particularly with authentication and decryption services to ensure only authorised boot codes are executed.
- It verifies the integrity of the subsequent stages, such as bootloader (UEFI) and the kernel, preventing unauthorised code execution. 

### MB1(MicroBoot1):

- This is the first and critical NVIDIA signed boot software component in the Jetson.
- This run on the BPMP to initialize essential hardware, **configure PINMUX, GPIO** via MB1-BCT and boot next stage MB2.
- It gets loaded into AOTZRAM (Always-on Trusted Zone).
- MB1 uses the MB1-BCT to set up the pad voltages, firewalls, and PMIC to enable VDD_CPU rail.
- MB1 also sets up the secure control registers (SCR).
- MB1 executes immediately after device resets preparing environment for MB2.

### MB1-BCT(MicroBoot1 - Boot Configuration Table):

- This is a critical configuration table loaded by MB1 to initialise hardware **GPIO/PINMUX** settings, configure PMIcs and setup storage devices during early boot.
- This ensures hardware is ready before CPU cores are fully active.
- This table is constructed by various configuration files such as pinmux, gpio etc.
- MB1-BCT is essential for custom carrier boards.

### MB2(MicroBoot2):

- This is another crucial NVIDIA proprietary bootloader applet running on the main CPU.
- It operates after MB1, managing initial hardware configuration, and detection device types, setting up memory, and loading subsequent boot stages (UEFI).
- It is responsible for detect the Jetson module type and configuring DRAM.
- MB2 Behaviours can be configured through MB2-BCT which control features like UART, ECC and memory layouts.

### ATF(Arm Trusted Firmware):

- It is a critical, low level secure firmware component that runs in highest exception level on ARMv8 CPUs.
- This provides secure foundation for **Trusted Exection Environment** (TEE), which facilitates secure communication between Linux and Secure Firmware.

### UEFI (Unified Extensible Firmware Interface):

- This is the initial program to run, that initialises hardware and transferring control to the OS.
- It manages boot order, supports booting from various devices.
- This also implement secure boot.


