Day 02 – Linux Architecture, Processes, and systemd
----------------------------------------------------------------
What We'll Learn Today
----------------------------------------------------------------
👉 If a car stops working and you only know how to drive, you panic.
👉 But if you understand the engine, fuel system, and battery — you troubleshoot confidently.

Similarly in Linux
• If a server crashes and you only know restart, you panic.
• But if you understand processes, memory, services, logs, and permissions, you solve the issue step-by-step.

________________________________________________________________
🐧 Linux Architecture – The Big Picture
----------------------------------------------------------------
Applications & User Programs
(Firefox, Docker, VS Code) → What users interact with


User Space
(Libraries, Shell, Tools) → Where programs run


System Calls  → Bridge between User Space & Kernel


Linux Kernel
(Process, Memory, Devices)  → Core brain of system


Hardware
(CPU, RAM, Disk, Network) → Physical components

____________________________________________________________________________________________________

🔍 Explanation of Each Layer
----------------------------------------------------------------------------------------------------
1️⃣ Applications & User Programs

Tools you directly use

Example: Browser, Docker, VS Code

Run in user space
____________________________________________________________________________________________________

2️⃣ User Space
----------------------------------------------------------------------------------------------------

Contains libraries and shell

Applications cannot directly access hardware

Must request services via system calls

____________________________________________________________________________________________________

3️⃣ System Calls
----------------------------------------------------------------------------------------------------

Interface between user space and kernel

Example:

open() → open a file

fork() → create process

read() → read data
____________________________________________________________________________________________________

4️⃣ Linux Kernel
----------------------------------------------------------------------------------------------------

Core of the operating system

Manages:

Processes

Memory

Devices

File systems

Security
____________________________________________________________________________________________________

5️⃣ Hardware
----------------------------------------------------------------------------------------------------
Physical components

Controlled only by the kernel
____________________________________________________________________________________________________

🐧 Core Components of Linux
----------------------------------------------------------------------------------------------------
1️⃣ The Linux Kernel (The Brain) 

Think of the Linux Kernel as the brain of the operating system 🧠

Just like your brain:

 • Controls your body

 • Makes decisions

 • Manages resources

The kernel controls everything inside the computer.
----------------------------------------------------------------------------------------------------

💡 What Does the Kernel Do? 
 1. Manages Processes 
 👉 The kernel decides which program runs, when it runs, and how much CPU time it gets.
 2. Manages Memory (RAM) 
 👉 The kernel allocates and controls RAM for programs so they run smoothly without interfering with each other.
 3. Manages Hardware
 👉 The kernel communicates with CPU, disk, network, and other devices so applications can use hardware safely and efficiently.
 4. Manages Files & Permissions
 The kernel controls who can read, write, or execute files to keep the system secure and organized.


----------------------------------------------------------------------------------------------------
🎯 One Line Summary

The Linux Kernel is the core program that manages hardware, processes, memory, and security — and makes the entire system run smoothly.
_____________________________________________________________________________________________________________

2️⃣ User Space (Where We Live) 
--------------------------------------------------------------------------------------------------------------
What is User Space?
User Space is the part of Linux where all applications and user programs run.

Why the separation?
Linux separates user space and kernel space to keep the system secure, stable, and controlled.

What Lives in User Space?

🖥️ Applications → Docker, Nginx, VS Code, Browser

💻 Shell → bash, zsh

🛠️ System Tools → ps, top, ls, grep

📚 Libraries → glibc and shared libraries

👤 User Processes → Any running program started by you

--------------------------------------------------------------------------------------------------------------
🎭 Simple Analogy:
User space is like customers, the kernel is the manager, and hardware is the vault — access is always controlled. 🚀
______________________________________________________________________________________________________________

3️⃣ Init System / systemd (The Startup Manager)
--------------------------------------------------------------------------------------------------------------
🔹What is Init?
systemd is the modern implementation of the init system used in most Linux distributions today.
It replaced the older SysV init system because it is:
→ aster
→ More efficient
→ Better at handling complex service dependencies
--------------------------------------------------------------------------------------------------------------
🔹 Why Does systemd Matter?
systemd plays a major role in system management:

✅ Starts and stops services (web servers, databases, SSH, Docker)

✅ Manages dependencies (ensures correct startup order)

✅ Automatically restarts failed services

✅ Handles centralized logging (via journalctl)

✅ Provides faster boot times compared to older init systems

For DevOps, this means:

→ Easier troubleshooting

→ Better service reliability

→ Less downtime during incidents 
--------------------------------------------------------------------------------------------------------------
🎭 Simple Analogy
systemd is like a stage manager who makes sure every service starts at the right time and keeps the show running smoothly. 🚀
______________________________________________________________________________________________________________

🐧 How Processes Work in Linux
--------------------------------------------------------------------------------------------------------------
🔹 What is a Process?

A process is simply a program that is currently running on your system.

When you execute a command or open an application, Linux creates a process for it.
--------------------------------------------------------------------------------------------------------------
🔑 Key Points About a Process in Linux

✅ A process is a running program

✅ Each process has a unique PID (Process ID)

✅ Every process is created by another process (Parent → Child)

✅ The kernel manages CPU and memory for each process

✅ A process can be in different states (running, sleeping, zombie, etc.)

✅ Multiple processes can run at the same time (multitasking)
--------------------------------------------------------------------------------------------------------------
🔄 Process Lifecycle in Linux

1️⃣ Creation (fork)
   ↓
2️⃣ Execution (exec)
   ↓
3️⃣ Running
   ↓
4️⃣ Waiting / Sleeping (if needed)
   ↓
5️⃣ Termination
--------------------------------------------------------------------------------------------------------------
How Are Processes Created in Linux?
In Linux, processes are created using a parent–child model.
-------------------------------------------------------------------------------------------------------------
🔹 Step 1️⃣: fork() – Create a Copy

A running process creates a new process using the fork() system call.

The new process is called the child process.

The original process is called the parent process.

The child gets a new PID.

👉 At this stage, the child is almost an exact copy of the parent.
______________________________________________________________________________________________________________
🔹 Step 2️⃣: exec() – Load a New Program

After fork(), the child usually calls exec().

exec() replaces the child’s memory with a new program.

Now the child runs a completely new application.

______________________________________________________________________________________________________________
🔹 Simple Flow
--------------------------------------------------------------------------------------------------------------
Parent Process
     ↓ (fork)
Child Process Created
     ↓ (exec)
New Program Starts Running
--------------------------------------------------------------------------------------------------------------
One Line Summary

Linux creates processes using fork() to copy a parent and exec() to run a new program. 🚀
--------------------------------------------------------------------------------------------------------------
🔄 Process States in Linux

A process can be in different states depending on what it is doing:

| State    | Symbol | What It Means                                              |
| -------- | ------ | ---------------------------------------------------------- |
| Running  | R      | Currently executing on the CPU                             |
| Sleeping | S      | Waiting for input/output or some event                     |
| Stopped  | T      | Paused manually or by a signal                             |
| Zombie   | Z      | Finished execution but parent hasn’t collected exit status |
| Dead     | X      | Fully terminated and removed from memory                   |
_____________________________________________________________________________________________________________
🎯 Quick Understanding
-------------------------------------------------------------------------------------------------------------
R → Doing work

S → Waiting

T → Paused

Z → Finished but not cleaned

X → Completely gone
-------------------------------------------------------------------------------------------------------------
Check process states:
ps aux
-------------------------------------------------------------------------------------------------------------
Process states show whether a program is running, waiting, paused, or finished in the Linux system. 🚀
______________________________________________________________________________________________________________
🔑 Key Takeaways for DevOps Engineers
✅ Linux has layers: Hardware → Kernel → User Space → Applications

✅ Kernel controls everything: Processes, memory, devices, file systems

✅ Processes are created using: fork() and exec()

✅ systemd is your service manager: Start, stop, monitor, troubleshoot

✅ Master systemctl & journalctl: Essential daily DevOps tools
______________________________________________________________________________________________________________
📌 Quick Reference Cheat Sheet
ps aux                    # List all processes
ps -ef                    # Alternative detailed format
top                       # Real-time CPU & memory usage
htop                      # Improved top (if installed)
kill <PID>                # Stop a process
kill -9 <PID>             # Force kill process
pgrep <name>              # Find process ID by name
pkill <name>              # Kill process by name
______________________________________________________________________________________________________________
⚙️ systemd Commands
systemctl start <service>
systemctl stop <service>
systemctl restart <service>
systemctl status <service>
systemctl enable <service>
systemctl disable <service>
systemctl list-units --type=service

journalctl -u <service>
journalctl -u <service> -f
systemctl daemon-reload

______________________________________________________________________________________________________________
🎯 DevOps Tip
 Best Way to Learn Linux 

don’t just read… practice daily.🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀