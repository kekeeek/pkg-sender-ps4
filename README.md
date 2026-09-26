PKG Sender v1.0

PKG Sender is a cross-platform desktop application (Windows, macOS, Linux) designed to simplify the transfer and installation of PKG files to a jailbroken PS4. It combines RPI, GoldHEN, and FTP functionality into one interface.

✨ Features
🎮 PS4 PKG Installation

PKG Sender supports two installation methods:

RPI (Remote Package Installer)
GoldHEN

The application automatically communicates with the PS4 using the selected installation method and serves the PKG directly from the computer.

🟢 GoldHEN

PKG Sender supports GoldHEN's package-installation system.

Supported GoldHEN communication includes:

GoldHEN detection
BinLoader communication
Payload injection
Package installation
Direct PKG streaming from the PC
Automatic communication with the local HTTP server

GoldHEN uses its supported network ports, including the default 9090 BinLoader port.

🔵 RPI

PKG Sender also supports the PS4 Remote Package Installer.

RPI communicates through its HTTP API and allows PKG installation directly from the PC.

The application can:

Detect the RPI service
Start a package installation
Serve the PKG from the computer
Monitor the installation
Display transfer progress
Stop an active transfer

The RPI installation service normally uses port 12800.

📦 PKG Library

PKG Sender includes a local PKG library.

PKG files can be added to the library from the computer using the file browser.

The library is designed to provide useful information about each package, including information such as:

PKG name
Content ID / CUSA
Version
Package size
Cover/icon when available

PKG Sender does not require the package to be copied into another special directory before installation.

The application works with the PKG file stored on the user's computer.

📡 Network Configuration

The application allows the user to specify the PS4 address and the appropriate communication port.

Example:

PS4 IP: 192.168.2.94

The computer and PS4 must be able to communicate over the local network.

For best performance, a wired Ethernet connection is recommended for the PC and PS4.

Wi-Fi can work, but transfer speed and stability depend on the network.

⚡ Transfer Speed

PKG Sender displays the current transfer speed while a package is being installed.

The progress system is designed to represent the actual transfer rather than simply animating the progress bar.

The displayed progress is based on the transfer information available from the installation protocol.

The application avoids artificially forcing the progress bar to move faster than the actual transfer.

📊 Transfer Progress

During an installation, PKG Sender displays:

Installation percentage
Current transfer speed
Current transfer state

The progress bar is intended to remain synchronized with the real package transfer.

The application also prevents the progress display from exceeding the actual package size.

❌ Cancel Transfer

An active installation can be cancelled using the Cancel button.

When cancelling a transfer:

The current operation is stopped locally.
Network connections are closed.
The application attempts to stop the corresponding PS4 task when supported.
The progress display is reset.
PKG Sender remains open and ready for another installation.

This means cancelling a transfer does not require restarting the application.

📁 FTP

PKG Sender includes a dedicated FTP section for GoldHEN.

GoldHEN's FTP server normally listens on:

Port: 2121

FTP is used to transfer PKG files directly to:

/data/pkg
Sending a PKG

The user can:

Enter the PS4 IP address.
Enter the FTP port.
Select a PKG from the local library.
Choose the destination.
Start the FTP transfer.

The application uses standard FTP communication over TCP.

It supports passive FTP data connections.

📂 /data/pkg Manager

PKG Sender contains a small dedicated section for the PS4's:

/data/pkg

directory.

This is not intended to be a full PS4 file manager.

The application only looks inside /data/pkg.

It can:

🔄 Refresh the directory
📦 Display PKG files currently present
🗑️ Delete PKG files
Automatically refresh the list after a successful FTP upload

The application does not provide browsing or management of unrelated PS4 directories.

🗑️ Delete PKG From PS4

PKG Sender can delete packages directly from:

/data/pkg

Each detected PKG has a delete action.

Before deletion, the application asks for confirmation.

After successful deletion, the package list can be refreshed to show the current contents of the directory.

🔄 Refresh

The Refresh button reconnects to the PS4 FTP server and checks:

/data/pkg

again.

This allows the user to see packages that were:

uploaded through PKG Sender
uploaded through another FTP client
deleted externally
added while PKG Sender was already open
🖥️ User Interface

PKG Sender uses a dark modern interface designed around PS4 homebrew workflows.

The interface contains the main functions needed for package installation and FTP management without requiring a separate FTP application.

The interface and behavior are identical across all supported operating systems.

The application interface is provided in:

English

🎨 PKG Sender Identity

PKG Sender uses its own custom application branding and icon.

The application icon represents the core purpose of the software:

PKG package → network transfer → PlayStation

The branding is independent from the default Electron icon.

🔌 Network Ports

The different services use different ports.

Function	Default port
RPI	12800
GoldHEN BinLoader	9090
GoldHEN FTP	2121
PKG HTTP server	Local PC port

The PKG HTTP server runs on the computer and provides the PS4 with access to the local PKG during installation.

The PS4 does not connect to the PC using the GoldHEN 9090 port for every operation. Each protocol has its own communication channel.

🌐 PC HTTP Server

For RPI and GoldHEN installation workflows, PKG Sender can start a local HTTP server on the PC.

The server makes the selected PKG accessible to the PS4.

Conceptually:

PS4
 │
 │ HTTP
 ▼
PKG Sender HTTP Server
 │
 ▼
Local .PKG file

The PKG does not need to be uploaded to a separate cloud service.

The PC serves the package directly across the local network.

📦 PKG Metadata

PKG Sender can inspect package metadata stored inside the PKG.

Depending on the package, information may include:

Content ID
CUSA identifier
Title
Version
Size
Category
Icon

This information is used by the library to make packages easier to identify.

🚀 Typical Workflow
RPI / GoldHEN installation
1. Connect the PS4

Make sure the PS4 and PC are connected to the same network.

2. Enter the PS4 IP

Example:

192.168.2.94
3. Add a PKG

Use the local file browser and select the .pkg file.

4. Select the package

Choose the package from the PKG library.

5. Start installation

PKG Sender communicates with the PS4 and starts the appropriate installation process.

6. Monitor progress

The interface displays the transfer percentage and speed.

7. Wait for completion

Once the PS4 finishes receiving/installing the package, the operation ends.

📡 FTP Workflow
1. Enable GoldHEN FTP

Start the FTP server on the PS4.

2. Enter the PS4 IP

Example:

192.168.2.94
3. Enter FTP port

Default:

2121
4. Select a PKG

Select a package from the PKG library.

5. Send

PKG Sender transfers the package to:

/data/pkg
6. Manage the package

After the upload, press Refresh to see the package in the /data/pkg list.

The package can then be deleted directly from PKG Sender if desired.

🛠️ Troubleshooting
PS4 cannot be detected

Check:

PS4 IP address
PC IP address
Same local network
Firewall settings (Windows Firewall / macOS Firewall / Linux ufw or iptables, depending on your OS)
GoldHEN/RPI service status
Correct communication port
FTP connection fails

Check that GoldHEN FTP is running.

Default:

PS4 IP: 192.168.x.x
FTP Port: 2121

Also check your operating system's firewall (Windows Firewall, macOS Firewall, or your Linux distribution's firewall) if the connection cannot be established.

FTP upload fails

Make sure:

/data/pkg

is accessible on the PS4.

Try pressing Refresh first.

If the directory does not exist or cannot be accessed, the FTP server may need to be restarted.

Installation stops

Check:

Network stability
Ethernet connection
Available PS4 storage
PKG integrity
GoldHEN/RPI status
Your operating system's firewall (Windows Firewall, macOS Firewall, or Linux firewall)

For large packages, a wired network is recommended.

macOS-specific note

The macOS build is not notarized/signed by Apple. On first launch, right-click the app and choose "Open", or allow it under System Settings → Privacy & Security.

Linux-specific note

On Linux, make sure the PKG Sender binary is executable before launching it:

chmod +x PKG-Sender

🔐 Security / Network Notes

PKG Sender is designed for use on a local network.

The HTTP server used for PKG transfer exposes the selected package to clients that can reach the configured PC server.

For this reason, avoid exposing the PKG Sender HTTP server directly to the public Internet.

Use PKG Sender on a trusted local network.

💻 Requirements
Windows
Windows 10 or newer
x64 PC
Local network connection
PS4 with the required homebrew environment
macOS
macOS 11 (Big Sur) or newer
Intel (x64) or Apple Silicon (arm64) Mac
Local network connection
PS4 with the required homebrew environment
Linux
A modern 64-bit Linux distribution
x64 PC
Local network connection
PS4 with the required homebrew environment
PS4

Depending on the installation method:

RPI service
or GoldHEN with the required services enabled
📜 Project

Project: PKG Sender
Version: 1.0
Platform: Windows, macOS, Linux
Interface: English

PKG Sender is designed as a simple all-in-one utility for managing local PS4 PKG transfers through RPI, GoldHEN and FTP.

⚠️ Disclaimer

PKG Sender is a network/package-transfer utility.

Users are responsible for ensuring that the PKG files they use are legally obtained and that they have the necessary rights to install or transfer them.

The software does not provide copyrighted games or PKG files 
