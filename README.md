<div align="center">


  # E.Box Windows Flush

  **A lightweight, native Win32 C++ utility to clean system caches, reset network stacks, and restore Windows performance.**

  [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
  [![Platform](https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011-0078D4.svg?logo=windows)](https://github.com/ElectronicBox/E.Box-Windows-Flush)
  [![Language](https://img.shields.io/badge/Language-C%2B%2B-00599C.svg?logo=cplusplus)](https://github.com/ElectronicBox/E.Box-Windows-Flush)
  [![Architecture](https://img.shields.io/badge/Architecture-x64-brightgreen.svg)]()

  ---

  [Key Features](#-key-features) • [Download](#-download) • [Tasks Included](#-tasks-included) • [How It Works](#-how-it-works)

</div>

<br>

## ⚡ Overview

**E.Box Windows Flush** is built from the ground up using the pure Win32 API and C++. Designed without heavy runtime dependencies or background bloat, it delivers direct system cleanup, socket resets, and cache maintenance safely and instantly — all from a single, dependency-free executable.

<br>

## 🚀 Key Features

* **⚡ Fast, Sequential Task Engine:** Selected tasks run one after another on a background worker thread with a live progress bar, so the UI never freezes.
* **🛡️ Native & Lightweight:** Zero external framework dependencies; pure Windows API UI components in a single `.exe`.
* **🌐 Network Stack Repair:** DNS flushing, Winsock/WinHTTP proxy resets, ARP & NetBIOS cache clears, and forced NTP time resynchronization.
* **🖼️ Explorer & Shell Fixes:** Clears icon and thumbnail caches by safely stopping and restarting Windows Explorer.
* **🧹 Deep Cache Flushing:** Cleans user/system `%TEMP%`, GPU shader caches (NVIDIA/AMD/Intel), Windows Update and Delivery Optimization caches, and font caches.
* **🔐 One-Time Elevation:** Requests Administrator privileges once at startup, then runs every task in-process — no repeated UAC prompts.
* **✔️ Safe by Design:** Only caches, logs and self-rebuilding system files are touched — never user documents, never restore points or shadow copies, never driver stores or installer caches that Windows needs for updates and uninstalls.

<br>

## ⬇️ Download

Ready-to-run x64 build (no installation, no dependencies):

**[E.Box Windows Flush.exe](dist/E.Box%20Windows%20Flush.exe)** — download it, then right-click → **Run as administrator**.

> **Note:** This is a closed-source project. The source code is not publicly available; only the compiled executable is distributed here.

<br>

## 🛠️ Tasks Included

| # | Task | What It Does |
| :---: | :--- | :--- |
| 1 | **Empty Windows Recycle Bin** | Empties the Recycle Bin on all drives and sweeps orphaned `$I*`/`$R*` entries |
| 2 | **Recent Files & Destinations** | Clears the user's Recent folder and jump-list destinations |
| 3 | **MRU Lists (RunMRU & TypedPaths)** | Removes Run-dialog and typed-path history from the registry |
| 4 | **GPU Shader Caches** | Clears NVIDIA (`DXCache`/`GLCache`), AMD (`DxCache`), Intel (`ShaderCache`) and `D3DSCache` |
| 5 | **User Temporary Files** | Recursively cleans `%TEMP%` |
| 6 | **System Temporary Files** | Recursively cleans `%WINDIR%\Temp` |
| 7 | **Performance Counters** | Re-registers system performance counters (`lodctr /R`) |
| 8 | **Flush System Clipboard** | Empties the Windows clipboard |
| 9 | **Clear Font Cache** | Stops the FontCache service, wipes the font cache, restarts the service |
| 10 | **Network Configuration & Winsock Reset** | `ipconfig /flushdns`, `netsh winhttp reset proxy`, `netsh winsock reset` |
| 11 | **Flush ARP & NetBIOS Caches** | `nbtstat -R`, `nbtstat -RR`, `arp -d *` |
| 12 | **Time with NTP Server** | Forces a time resync (`w32tm /resync /force`) |
| 13 | **Internet Proxy Settings** | Disables the WinINET proxy and removes stale `ProxyServer`/`ProxyOverride` values |
| 14 | **Windows Update Cache** | Stops `wuauserv`, clears `SoftwareDistribution\Download`, restarts the service |
| 15 | **Delivery Optimization Cache** | Clears `ProgramData\Microsoft\Network\Downloader` |
| 16 | **Windows Error Reports** | Clears WER `ReportArchive` and `ReportQueue` |
| 17 | **Memory Dumps & Minidumps** | Deletes `MEMORY.DMP` and the `Minidump` folder |
| 18 | **Thumbnail Cache** | Restarts Explorer and wipes the Explorer icon/thumbnail cache |
| 19 | **Application Crash Dumps** | Clears the WER `Temp` folder |
| 20 | **Windows Live Kernel Reports** | Clears `Windows\LiveKernelReports` |
| 21 | **CBS & DISM Logs** | Clears `Windows\Logs\CBS` and `Windows\Logs\DISM` |
| 22 | **NVIDIA Driver Download Artifacts** | Clears the NVIDIA downloader folder |
| 23 | **AMD Installer Files in C:\AMD** | Clears `C:\AMD` |
| 24 | **User Crash Dumps** | Clears `%LOCALAPPDATA%\CrashDumps` |
| 25 | **Windows Prefetch** | Clears `Windows\Prefetch` (rebuilds automatically) |
| 26 | **Component Store Cleanup (WinSxS)** | Official Microsoft WinSxS cleanup via `DISM /StartComponentCleanup` — removes only superseded components |
| 27 | **Crypto Catalog Cache (catroot2)** | Rebuilds the `System32\catroot2` catalog cache |
| 28 | **Windows Upgrade Files** | Removes `Windows.old`, `$WINDOWS.~BT` and `Panther` |
| 29 | **System Logs** | Clears everything under `Windows\Logs` |
| 30 | **Event Logs (Application & System)** | Clears the Application and System event logs |
| 31 | **Browser Cookies (Edge & Chrome)** | Removes Edge/Chrome cookie databases including WAL sidecars (closes the browsers first) |
| 32 | **Restart Windows Explorer** | Force-restarts `explorer.exe` to refresh the shell |

<br>

## ⚙️ How It Works

1. The app elevates to Administrator once at launch (single UAC prompt).
2. Tick any combination of tasks (or **Select All**) and press **Run Selected Tasks**.
3. Tasks execute in order on a worker thread; each checkbox grays out while its task runs and is checked off when it completes.
4. When the run finishes, all checkboxes reset so any task can be run again immediately.

> **Note:** Some tasks (e.g. Winsock reset) require a reboot to take full effect.

<br>

## 📜 License

Distributed under the MIT License. See [LICENSE](LICENSE) for more information.
