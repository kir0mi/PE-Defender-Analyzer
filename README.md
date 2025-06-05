# PE-Defender-Analyzer - DLL-Plugin-for-PEiD

Overview
PE Defender Analyzer is a PowerBasic-written plugin for PEiD that examines Windows executable files (PE files) for various defense mechanisms and anomalies. The plugin provides a detailed report on found protection techniques, packers, and suspicious file characteristics.

Key Features
1. Packer and Protector Detection
Scans files for signatures of over 60 known packers (UPX, ASProtect, Themida, VMProtect, etc.)

Checks section names for packer-specific naming patterns

Searches entire file for packer signatures

2. Entropy Analysis
Calculates file entropy to detect compressed or encrypted data

Interprets entropy levels:

High (>7.0) - likely packed or encrypted

Medium (6.0-7.0) - possible compression

Low (<6.0) - probably uncompressed data

3. Anti-Debug Technique Detection
Detects 10+ different anti-debugging techniques:

Debugger presence checks (IsDebuggerPresent)

PEB.BeingDebugged checks

NtGlobalFlag checks

Breakpoint detection (INT3)

Infinite loops

SEH tricks

Direct API calls (obfuscation)

4. Anti-VM Technique Detection
Identifies 25+ virtual machine detection methods:

CPUID instructions

VMware, VirtualBox, Hyper-V specific checks

Hardware port checks

MAC address verification

BIOS string checks

Virtual machine driver detection

5. Anti-Sandbox Technique Detection
Detects 20+ sandbox evasion techniques:

Sandbox name checks (Cuckoo, JoeBox etc.)

RAM disk checks

Memory size verification

Delay/sleep detection

Suspicious behavior checks

Timeout verification

Analysis environment driver detection

6. Shellcode Detection
Identifies shellcode patterns:

CALL with relative addresses

JMP + NOP sled

PUSHAD/POPAD

Register zeroing

Position-independent code

System calls (INT 80h, SYSCALL)

Decryptors (for polymorphic code)

Analyzes code section entropy

7. PE Header Anomaly Analysis
Checks SizeOfImage discrepancies

Looks for section "holes"

Verifies suspicious OptionalHeader values

Detects section overlaps

Examines unusual characteristic flags

Analyzes import table

Verifies checksums

Output Format
The plugin generates a structured text report saved in a file with the same name as the analyzed file but with "_analysis_report.txt" suffix. The report contains these sections:

[PACKER DETECTION] - packer detection results

[ENTROPY ANALYSIS] - file entropy analysis

[ANTI-DEBUG TECHNIQUES] - detected anti-debug techniques

[ANTI-VM TECHNIQUES DETECTION] - virtual machine detection methods

[ANTI-SANDBOX TECHNIQUES DETECTION] - sandbox evasion techniques

[SHELLCODE DETECTION] - shellcode indicators

[PE HEADER ANALYSIS] - PE header anomalies

Technical Details
Uses PEiD's plugin API for integration

Works with PE files via memory-mapped files

Employs signature scanning and heuristic methods

Supports both 32-bit and 64-bit PE files

Written in PowerBasic using Win32 API

Usage
Install the DLL in PEiD's plugins folder

Run PEiD and select a file to analyze

The plugin automatically creates a report in the same folder as the analyzed file

A message box shows the path to the generated report

This plugin is particularly useful for analyzing malware and protected applications, helping to quickly identify used protection and packing techniques.
