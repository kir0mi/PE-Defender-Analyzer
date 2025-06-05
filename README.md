# PE Defender Analyzer 

![PEiD Plugin](https://img.shields.io/badge/PEiD-Plugin-blue) 
![PowerBasic](https://img.shields.io/badge/PowerBasic-DLL-green)

**A PEiD plugin for advanced executable analysis**  
*Detects packers, anti-analysis techniques, and PE anomalies with precision*

## Features

### **Packer & Protector Detection**
- **60+ packer signatures** (UPX, ASProtect, Themida, VMProtect, etc.)
- Section name pattern matching
- Full file signature scans

### **Entropy Analysis**
- **Entropy scoring** with interpretation:

  - 6.0-7.0 → Possible compression
  - <6.0 → Probably raw data
  - >7.0 → Likely packed/encrypted

### **Anti-Analysis Detection**
- **Anti-Debug**:
  - IsDebuggerPresent checks
  - PEB/NtGlobalFlag inspection
  - INT3/SEH tricks detection
  
- **Anti-VM** (25+ techniques):
  - CPUID fingerprinting
  - VMware/VirtualBox/Hyper-V specific checks
  - Hardware/MAC/BIOS verification

- **Anti-Sandbox** (20+ techniques):
  - Sandbox process/driver detection
  - Environment fingerprinting
  - Timing/behavior checks

### **Shellcode Identification**
- Position-independent code patterns
- Common stub signatures
- Polymorphic code indicators
- Code section entropy analysis

### **PE Header Forensics**
- Structural anomalies
- Section inconsistencies
- Import table verification
- Checksum validation

## Technical Implementation
- **PEiD plugin architecture**
- Memory-mapped file analysis
- Hybrid signature/heuristic detection
- Win32 API powered (PowerBasic)

## Installation
1. Place DLL in PEiD's `plugins` folder
2. Launch PEiD and analyze target file
3. **Report** generates automatically as `[filename]_analysis_report.txt`
