# DBus Message Bus System

- IPC - **Inter Process Communication** that allows communication between two or more processes.
- Allows communication in a distributed environment either in a single system or different systems.
- It is simple, standard and secure communication, allowing us to eliminate communication error prone alternatives such as `sockets` or `pipes`.
- DBus can be used with several programming languages such as C, C++, Python and more.
- Allows building a messaging system for system-wide events and notifications.

### Components:

- It is a client server architecture.
- `Server` acts as the message bus and `Client` sending and receiving messages.
- The `Server` maintains registry of all available services and objects.
- The `Client` can access these services and objects through the server.
- DBus uses a modular architecture. At the core, the **message bus daemon**, is responsible for managing the communication between different processes.
- Applications can use client libraries to provide an API for sending and receiving messages, registering services and listening to events.
- Service providers register themselves with the message bus daemon, enabling other applications to access them.

### Using DBus:

- Common use case of DBus is to interact with system services.
- Most Desktop Environments (GNOME, Kde, xfce) use DBus to facilitate communication between processes in their environment.