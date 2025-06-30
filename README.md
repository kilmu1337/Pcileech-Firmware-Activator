# PCILeech Firmware Activator

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![FPGA](https://img.shields.io/badge/FPGA-Xilinx-orange.svg)](https://www.xilinx.com/)
[![SystemVerilog](https://img.shields.io/badge/language-SystemVerilog-green.svg)](https://en.wikipedia.org/wiki/SystemVerilog)

## 🔐 PCILeech Unlock Module (Core Feature)
**The main contributor to this Module is AceKingSuited.**

The `pcileech_unlock` module is the heart of this firmware activator, providing a secure hardware-based authentication system.

### Key Features:

- **Magic Key Authentication**: Uses a 64-bit activation key (`0xDEADC0DEDEADC0DE`)
- **Timestamp Validation**: Records activation time for audit purposes
- **State Machine Protection**: Prevents bypass attempts and unauthorized access
- **Real-time Processing**: Handles incoming TLP data streams in real-time

### Technical Specifications:

```systemverilog
// Activation Parameters
localparam activate_key = 64'hDEADC0DEDEADC0DE;  // Magic activation key
input  wire[31:0]  i_data      // Input data stream
input  wire        i_valid     // Data valid signal
input  wire        i_last      // Last data indicator
output bit         o_unlock    // Unlock status output
```

### Security Architecture:

1. **Data Validation**: Continuously monitors incoming PCIe TLP data
2. **Key Matching**: Compares received data against the hardcoded activation key
3. **State Management**: Once unlocked, maintains state until system reset
4. **Audit Trail**: Captures timestamp of successful activation events

## ⚠️ Legal Notice

**IMPORTANT**: This tool is designed for authorized security research and penetration testing only. Users must:

- Have explicit permission to test target systems
- Comply with all applicable laws and regulations
- Use responsibly and ethically
- Respect intellectual property rights

The authors are not responsible for any misuse of this software.

## 🙏 Acknowledgments

- **Ulf Frisk** - Original PCILeech framework
- **AceKingSuited** - Main contributor

## 📄 Note

This project is actually a simple example project. You should apply some encryption obfuscation to the activate_key.

I am considering selling my complete pcileech activator code set at $400, including PCILeech-side encryption obfuscation and software-side (custom UI). If you are interested, please contact me at: [https://discord.gg/KilmuDMA](https://discord.gg/KilmuDMA)