# EDK II - EFI Developement Kit

1. EDK - II is a modern, feature rich, cross-platform firmware development environment 

In order to build EFI application, we have to setup the EDK II build environment.

1. Install the [dependencies](https://github.com/tianocore/tianocore.github.io/wiki/Using-EDK-II-with-Native-GCC#ubuntu-2004-lts).
2. Setup the build environment by following the [instructions](https://github.com/tianocore/tianocore.github.io/wiki/Common-instructions#common-edk-ii-build-instructions-for-linux).
3. Export the below variables if the `edksetup.sh` file fails to do so.
```
export WORKSPACE=/home/rmcl_robotics/projects/edk2; 
export EDK_TOOLS_PATH=/home/rmcl_robotics/projects/edk2/BaseTools; 
export CONF_PATH=/home/rmcl_robotics/projects/edk2/Conf; 
export PYTHON_COMMAND=python3;
export PATH="$PWD/BaseTools/BinWrappers/PosixLike:$PATH";
```
4. Then create your EFI apps in the `EmulatorPkg` and build it using the `build.sh` script in the same directory after adding your app into the `EmulatorPkg.dsc` and `EmulatorPkg.fdf`.
