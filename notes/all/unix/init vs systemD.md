
### **Overview: Init Systems and Systemd**

In Linux, **init systems** manage system processes, especially during startup and shutdown. The two main init systems in use today are **SysV init** and **Systemd**.

---

### **Init System Basics**
The init system is the first process started by the kernel and has PID 1. It is responsible for initializing the system, managing background services, and ultimately shutting down the system. Older systems used **SysV init**, a straightforward but limited system that operates in run levels:

- **Run Levels**:
  - `0`: Halt (shutdown)
  - `1`: Single-user mode
  - `2-5`: Multi-user modes with variations
  - `6`: Reboot

SysV init worked by starting and stopping services based on these run levels, but it lacked flexibility, causing slower boot times and requiring more manual configuration.

---

### **Systemd: The Modern Init System**

**Systemd** was developed as an advanced init system that overcomes SysV’s limitations. It uses **units** (unit files) to manage services, processes, and even devices, providing parallelization and dependency handling to speed up boot times. Instead of run levels, it uses **targets**—logical groupings of services—to bring the system into specific states.

#### Key Systemd Components:

- **Service Units (`.service` files)**: Define a service's startup commands, conditions, and dependencies.
- **Socket Units (`.socket` files)**: Enable on-demand service activation by listening on specific network ports or file sockets, launching the service only when a connection is made.
- **Target Units**: Replace SysV run levels. Examples include:
  - `multi-user.target`: Multi-user, no GUI (similar to SysV level 3).
  - `graphical.target`: Multi-user with a graphical interface (similar to SysV level 5).
  - `rescue.target`: Minimal single-user mode for recovery (like level 1).

---

### **Managing Services with Systemd**

Systemd simplifies service management by providing uniform commands to control services and targets:

- **Starting a Service**: `systemctl start <service>.service`
- **Enabling on Boot**: `systemctl enable <service>.service`
- **Checking Status**: `systemctl status <service>.service`
- **Stopping and Restarting**: `systemctl stop/restart <service>.service`

With **Systemd**, you can create and modify `.service` and `.socket` files in `/etc/systemd/system/` to define custom services, specify dependencies, and handle restart policies if a service crashes. 

**Example: Basic Service File**:
```ini
[Unit]
Description=Example Service
After=network.target

[Service]
ExecStart=/path/to/executable
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

---

### **Targets in Systemd**

Targets help manage groups of services, allowing flexible boot configurations:

- **Default Target**: The system’s boot target, usually set to `multi-user.target` (for servers) or `graphical.target` (for desktops).
  - Set default target: `systemctl set-default <target>`
  - Switch target: `systemctl isolate <target>`

You can create custom targets to start specific services as needed.

---

### **Using `pstree` to Visualize Processes**

The `pstree` command displays processes in a tree structure, showing parent-child relationships. This can be particularly useful for visualizing which processes are managed by `systemd` and troubleshooting if you’re looking at specific user processes.

**Basic Usage**:
```bash
pstree          # Displays the tree structure of all processes
pstree -p       # Shows process IDs (PIDs)
pstree <user>   # Filters by specific user
```

---

### **Systemd Troubleshooting and Logs**

**Systemd** logs output through `journalctl`, a powerful logging tool for monitoring services:

- **View Logs for a Service**: `journalctl -u <service>.service`
- **Check Last Boot Logs**: `journalctl -b`
- **Live Logs**: `journalctl -f`

If a service fails, `systemctl status <service>.service` provides immediate details, while `journalctl` offers in-depth log access to diagnose issues.

---

In summary, **Systemd** brings a modern, efficient approach to service management with parallel startup, robust logging, and easy-to-use service files, making it the preferred init system over SysV in most Linux distributions today.



In a Systemd service unit file, the `Before=` and `After=` directives define the **ordering dependencies** between services. These directives control the order in which services are started or stopped, specifying whether the current service should be launched before or after other services or targets.

### **How `Before=` and `After=` Work**

- **`Before=`**: If you specify a service or target in the `Before=` line, Systemd will ensure that the current service starts **before** the listed services or targets.
- **`After=`**: Conversely, if you specify a service or target in the `After=` line, Systemd will ensure that the current service starts **after** the listed services or targets.

These directives do **not guarantee that the listed services will start**—they only specify the order if those services are also started as part of a target. 

### **Example of `Before=` and `After=`**

Suppose you have a web application service that depends on the network being up before it can start. You can use `After=network.target` to ensure that the network is initialized first.

Here’s an example of a custom `.service` file with `Before=` and `After=`:

```ini
[Unit]
Description=My Web Application
After=network.target
Before=apache2.service

[Service]
ExecStart=/path/to/my_web_app
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

- **`After=network.target`**: This ensures the network is up and running before `my_web_app` starts.
- **`Before=apache2.service`**: This means `my_web_app` should be started before `apache2.service` (the Apache web server) if Apache is also being started.

### **Common Use Cases for `Before=` and `After=`**

1. **Networking Services**:
   - Use `After=network.target` in applications that require network connectivity.
   - For databases, use `Before=` to ensure that the database service starts before dependent applications.

2. **Application Dependencies**:
   - When multiple services rely on a database, start the database first with `After=` in the dependent services, and potentially `Before=` in the database service.

3. **Custom Targets**:
   - If you create a custom target for several services, `Before=` and `After=` ensure that the services start in the proper sequence.

### **Example for Practical Setup**

Consider a scenario with three services: `database.service`, `backend.service`, and `frontend.service`. You want the startup order to be **database** → **backend** → **frontend**.

- **`database.service`**:
  ```ini
  [Unit]
  Description=Database Service
  Before=backend.service
  ```

- **`backend.service`**:
  ```ini
  [Unit]
  Description=Backend Service
  After=database.service
  Before=frontend.service
  ```

- **`frontend.service`**:
  ```ini
  [Unit]
  Description=Frontend Service
  After=backend.service
  ```

With this setup:
- `database.service` starts first.
- Once it’s active, `backend.service` starts.
- Finally, `frontend.service` starts after the backend is ready.

### **Summary**

- `Before=` and `After=` order service startups relative to each other.
- They only affect the order—not whether the services start.
- Use `Before=` for services that need to be fully started first, and `After=` for services that depend on other services being initialized beforehand.






![[Pasted image 20241108145959.png]]


test comes After A
test comes before B ===> its common to assume the opposite!
test wants: iheb yestamml ama ken mal9ach mayaaml chy
test requires: iheb yestaaml ama ken mal9ahech mayekhdmlna chy!  : so here test needs to run AFTER j yelanca
conflicts : arret dun service ; el ufw lezmou youfe 9bal el test 



![[Pasted image 20241108152530.png]]

