Water Defender 6.5(🦀)

Hash-Based Real-Time Threat Detection (Educational Edition)

Water Defender 6.5 is a Python-based, single-binary endpoint monitoring utility compiled with PyInstaller. Designed strictly for security research and academic experimentation, it provides user-mode real-time protection (RTP) through filesystem event monitoring and SHA-256 hash verification.

Platform Support

• Supported: Windows 10, Windows 11 (x64)

• Unsupported: Windows 8.1 and earlier versions

Architecture Overview

• Language: Python 3.x

• Packaging: Standalone EXE via PyInstaller (--onefile)

• Monitoring Engine: Watchdog (ReadDirectoryChangesW backend)

• Hashing Algorithm: SHA-256 (FIPS 180-4 compliant)

• UI Framework: Tkinter (Custom GUI)

• Privilege Level: User-mode (No kernel drivers / ELAM integration)

Core Capabilities

1. Real-Time Protection (RTP)

• Event Monitoring: Utilizes Watchdog to hook into the Windows API (ReadDirectoryChangesW) for low-latency filesystem event detection.

• Scope:

  ◦ C:\ Drive: Targets high-risk user directories (Downloads, Desktop, Documents, Pictures, AppData, %TEMP%). System directories (Windows, Program Files, etc.) are explicitly excluded to prevent system instability.

  ◦ Removable Media: Automatic detection and monitoring of newly connected USB drives and secondary volumes.

• Debouncing: Implements a 2-second event cooldown per file path to prevent recursive scan loops and resource exhaustion.

2. Static Hash Analysis

• Signature Database: Contains an embedded, read-only set of known malware SHA-256 hashes.

• Verification: Upon file creation, modification, or move events, the engine calculates the SHA-256 hash and performs an immediate lookup against the internal database.

• File Handling: Ignores non-executable extensions and files exceeding 50MB to optimize I/O performance.

3. Automated Response

• Quarantine: Detected threats are immediately moved to a protected directory (%USERPROFILE%\WaterDefender_Quarantine) to isolate them from the system.

• Logging: All events (scans, detections, errors) are streamed to a live GUI log with timestamping and color-coded severity levels.

4. Manual Scanning Utilities

• File Scan: On-demand analysis of user-selected files.

• Folder Scan: Recursive traversal of directories with blacklist filtering.

• Full Disk Scan: Comprehensive system sweep (excluding system-protected paths).

Usage Instructions

Water Defender 6.5 is a standalone executable and requires no installation.

1. Extract Water-Defender 6.5.exe.

2. Select "Run as administrator" (Required for full filesystem access and quarantine permissions).

3. Click "START SHIELD" in the GUI to initialize real-time monitoring.

Note: The GUI will automatically detect and list all currently mounted volumes. USB drives will be added to the watch list dynamically upon insertion.

Known Limitations & Technical Notes

• User-Mode Constraint: As a Python/Watchdog implementation, Water Defender operates in user-mode. It cannot prevent a file from being read or executed before the hash calculation is complete. This creates a "race condition" inherent to non-kernel solutions.

• Performance Impact: High-frequency file operations (e.g., during software installation or compilation) may cause event queue backlog or slight system latency.

• False Positives: PyInstaller executables are frequently flagged by heuristic-based antivirus engines. This is a known industry occurrence and does not indicate malicious behavior.

• No Network Protection: This tool does not monitor network traffic, registry changes, or process injection.

• Signature Updates: The hash database is static and embedded at compile time. It does not support OTA (Over-The-Air) signature updates.

Important Disclaimer

This software is provided for EDUCATIONAL PURPOSES ONLY.

• Water Defender 6.5 is NOT a replacement for commercial Endpoint Detection and Response (EDR) or Antivirus solutions.

• The author assumes NO LIABILITY for system damage, data loss, security breaches, or any consequences arising from the use of this tool.

• Use at your own risk. Do not deploy in production environments.

License

Copyright © 2026 [ZZTalksComputers]. All rights reserved.

This software is provided "as is", without warranty of any kind, express or implied. Redistribution for educational purposes is permitted provided this copyright notice is included.

Downloads
All releases and source code are available at the official repository:
GitHub Repository:

https://github.com/ZZZ-cpu-svg/waterdefender/releases
Please download from the Releases section to obtain stable builds.
A mirror download is also available for faster access: https://1854158522.share.123pan.cn/123pan/DJiXvd-LqG0h?pwd=UGtg#

------

Water Defender Team - Security Research Division

Built with Python, Watchdog, Tkinter, and PyInstaller.

