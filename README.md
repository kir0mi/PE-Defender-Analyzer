# PE Defender Analyzer  

![PEiD Plugin](https://img.shields.io/badge/PEiD-Plugin-blue) 
![PowerBasic](https://img.shields.io/badge/PowerBasic-DLL-green)

Advanced PE analysis plugin for PEiD that detects packers, anti-analysis techniques, and PE anomalies.

## 🔍 Features

### 🧰 **Packer Detection**
- **60+ signatures** (UPX, Themida, VMProtect, ASProtect, etc.)
- Section name analysis
- Deep file scanning

### 📊 **Entropy Analysis**
- Calculates file entropy:
  - `>7.0` → Likely **packed/encrypted**
  - `6.0-7.0` → Possible **compression** 
  - `<6.0` → Probably **raw data**

### 🚫 **Anti-Analysis Detection**
| Technique Type       | Examples Detected |
|----------------------|-------------------|
| **Anti-Debug**       | IsDebuggerPresent, PEB checks, INT3 traps |
| **Anti-VM**          | CPUID checks, VMware/VirtualBox detection |
| **Anti-Sandbox**     | Sandbox names, RAM checks, sleep detection |

### ⚠️ **PE Anomalies**
- Header inconsistencies
- Suspicious section characteristics
- Import table anomalies
- Checksum verification

## 📥 Installation
1. Place DLL in PEiD's `plugins` folder
2. Launch PEiD and analyze target file
3. Report saves automatically as `[filename]_analysis_report.txt`

## 📝 Sample Report
```text
[PACKER DETECTION]
- Detected: UPX (section UPX0)

[ENTROPY ANALYSIS]
File entropy: 7.89 - High entropy

[ANTI-DEBUG TECHNIQUES]
- PEB.BeingDebugged check
- INT3 breakpoint detection

[PE HEADER ANALYSIS]
- Suspicious SizeOfImage discrepancy
