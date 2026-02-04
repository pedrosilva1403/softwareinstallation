# softwareinstallation
Sofwtare Installation using Shell


# General Description – Remote Management Script
This script was designed to remotely manage software installations and uninstallations on Windows computers in a standardized, secure, and unattended way, using native Windows and PowerShell technologies.
🔹 Purpose
The main goal of this script is to allow a technician to install or remove software on a remote computer without requiring physical access or interactive login on the target machine.

🔹 Execution Flow
When the script is executed, it follows this sequence:


Automatic privilege elevation

If the script is not running with administrative privileges, it automatically restarts itself with elevated permissions to ensure all required actions can be performed.



Target computer definition

The user is prompted to enter the hostname of the destination computer where the actions will be executed.



Authentication

An administrative credential is requested.
This credential is used for:

Accessing the administrative network share (\\HOSTNAME\d$)
Executing commands remotely via WMI/DCOM





Interactive menu

A simple, menu‑driven interface allows the user to choose between:

Software installation
Software uninstallation
Exiting the script






🔹 Installation Logic
All installations follow a consistent and controlled process:

Installation files are copied to the local disk of the remote computer (D:\Instaladores)
The installer is executed remotely and silently, without user interaction
The script monitors the process until completion
After the installation finishes, the copied files are automatically removed from the target machine

This approach minimizes network dependency during installation, improves reliability, and keeps the destination system clean.

🔹 Uninstallation Logic
When the uninstallation option is selected:

The script queries the Windows Registry of the remote computer, checking both 32‑bit and 64‑bit locations
It locates the installed software based on its display name
The removal is performed silently, using the appropriate uninstall method
After execution, the script verifies whether the software was successfully removed


🔹 Logging
All actions performed by the script are fully logged:

A detailed log file is created automatically in the Logs folder
The log includes:

Executed actions
Commands sent to the remote computer
Return codes and process information
Errors and exception details


This ensures traceability, auditing, and easier troubleshooting


🔹 Security and Reliability
The script was built following best practices:

Secure credential handling
Administrative privilege enforcement
Controlled remote execution
Error handling and exception logging
User confirmations before critical operations


🔹 Intended Audience
This script is suitable for:

Service Desk teams
IT support technicians
System administrators
Corporate environments with standardized software deployment
