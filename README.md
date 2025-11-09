# ESP32-C3 Ultra Edition v4.1

![Version](https://img.shields.io/badge/version-1.0-blue.svg)
![Platform](https://img.shields.io/badge/platform-ESP32--C3-green.svg)
![License](https://img.shields.io/badge/license-MIT-orange.svg)

A powerful multifunctional ESP32-C3 device featuring AI integration, wireless mesh networking, battery monitoring, and advanced power management.

## ✨ Features

### 🤖 AI Integration
- **Gemini AI Chat**: Integrated with Google's Gemini 2.0 Flash model
- Dual API key support for redundancy
- Real-time AI response with loading animations
- Custom keyboard input system

### 📡 Connectivity
- **WiFi Manager**: Easy network scanning and connection
- Auto-save credentials with preferences
- WiFi signal strength indicator
- Auto-off timer to save battery

### 💬 ESP-NOW Mesh Networking
- Peer-to-peer messaging without internet
- Support up to 5 peers
- Built-in inbox with read/unread status
- Peer management (add, rename, delete)
- MAC address-based identification

### 🔋 Advanced Power Management
- **Battery Guardian**: Real-time voltage and percentage monitoring
- Battery drain rate calculation
- Estimated time remaining
- Battery leak detection
- Charging status indicator
- Historical battery graph (60 data points)

### 🔌 Power Consumption Monitor
- Real-time power usage breakdown
- WiFi, Display, and CPU consumption tracking
- Visual power consumption graph
- Total power draw calculation

### 🧮 Calculator
- Full 4-function calculator (+ - × ÷)
- Intuitive grid-based interface
- Decimal support
- Error handling

### ⚡ System Monitoring
- Heap memory tracking with warnings
- CPU frequency and temperature monitoring
- Loop performance counter
- Developer mode with real-time diagnostics

### 🧘 Zen Mode
- Minimalist breathing meditation interface
- Automatic WiFi disconnect
- Timer with breathing visualization
- Battery-efficient operation

### 🎨 Display Features
- 128x64 OLED display (SSD1306)
- Custom icons for each menu
- Smooth animations
- Adjustable font size and animation speed
- Breadcrumb navigation
- Progress bars and loading animations

### 💡 LED Indicators
- **Heartbeat**: Main menu idle state
- **Pulse**: Loading and charging states
- **Breathing**: Low-power states
- **Blink patterns**: Warnings and notifications
- **Rainbow**: System info display
- Context-aware LED feedback

## 🛠️ Hardware Requirements

### Main Components
- **ESP32-C3 SuperMini** development board
- **OLED Display**: SSD1306 128x64 (I2C)
- **6 Push Buttons** for navigation
- **Battery**: LiPo/Li-ion with monitoring circuit

### Pin Configuration
```
OLED Display:
- SDA: GPIO 20
- SCL: GPIO 21
- Address: 0x3C

Buttons:
- UP: GPIO 5
- DOWN: GPIO 6
- LEFT: GPIO 3
- RIGHT: GPIO 4
- SELECT: GPIO 9
- BACK: GPIO 2

System:
- LED_BUILTIN: GPIO 8
- BATTERY_PIN: GPIO 0 (ADC)
- CHARGING_PIN: GPIO 1 (ADC)
```

### Circuit Notes
- Voltage divider ratio: 2.0 (for battery monitoring)
- Battery range: 3.3V - 4.2V
- All buttons use internal pull-up resistors

## 📦 Dependencies

Install these libraries via Arduino Library Manager:

```
- Adafruit GFX Library
- Adafruit SSD1306
- ArduinoJson
- ESP32 Board Support (v2.0.0+)
```

## 🚀 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/silentprojectid/AI-pocket.git
   cd AI-pocket
   ```

2. **Open in Arduino IDE**
   - Install ESP32 board support
   - Select board: "ESP32C3 Dev Module"
   - Select correct COM port

3. **Configure API Keys** (Optional)
   - Edit the code to add your Gemini API keys:
   ```cpp
   const char* geminiApiKey1 = "YOUR_API_KEY_1";
   const char* geminiApiKey2 = "YOUR_API_KEY_2";
   ```

4. **Upload**
   - Compile and upload to your ESP32-C3
   - Open Serial Monitor (115200 baud) to see device MAC address

## 📖 Usage Guide

### First Boot
1. Device will attempt to connect to saved WiFi
2. If no credentials, WiFi menu opens automatically
3. Navigate using UP/DOWN buttons
4. SELECT to confirm, BACK to go back

### Main Menu Navigation
- **Chat AI**: Talk to Gemini AI (requires WiFi)
- **WiFi**: Scan and connect to networks
- **Calculator**: Basic arithmetic operations
- **Power**: Battery and power monitoring
- **Battery Guard**: Advanced battery analytics
- **ESP-NOW**: Mesh messaging (no WiFi needed)
- **Settings**: Configure device preferences
- **About**: Device information

### ESP-NOW Messaging
1. Go to ESP-NOW > Manage Peers
2. Add peer using their MAC address
3. Give peer a friendly name
4. Send messages via ESP-NOW > Send Message
5. Check inbox for received messages

### Keyboard Input
- Use arrow buttons to navigate
- SELECT to type character
- `#` key to switch keyboard layouts:
  - Lowercase (a-z)
  - Uppercase (A-Z)
  - Numbers/Symbols
  - Hex (for MAC addresses)
- `<` to backspace
- `OK` to submit

## ⚙️ Configuration

### WiFi Auto-Off
Enable in Settings to disconnect WiFi after 5 minutes of inactivity (saves battery).

### Display Settings
- **Font Size**: 1 or 2
- **Animation Speed**: 50-300ms

### Developer Mode
Enables real-time system diagnostics including:
- Heap usage monitoring
- CPU temperature
- Loop performance
- Low memory warnings

## 🔋 Battery Monitoring

The device tracks:
- Current voltage and percentage
- Charging status
- Drain rate (%/minute)
- Time remaining until empty/full
- 60-minute historical graph
- Battery leak detection

### Battery Leak Warning
If drain rate exceeds 2%/minute, the device displays a warning alert.

## 📊 Power Consumption

Typical power draw:
- **WiFi Connected**: ~80mA
- **WiFi Scanning**: ~120mA
- **WiFi Off**: 0mA
- **Display**: ~20mA
- **CPU (80-160MHz)**: 30-60mA

Use Power Monitor to see real-time breakdown.

## 🐛 Troubleshooting

### Device won't connect to WiFi
- Check SSID and password
- Ensure 2.4GHz network (ESP32-C3 doesn't support 5GHz)
- Try "Forget Network" and reconnect

### Low memory warnings
- Normal during heavy WiFi/AI usage
- Restart device if persistent
- Avoid leaving AI responses with very long text

### ESP-NOW messages not sending
- Verify peer MAC address format (XX:XX:XX:XX:XX:XX)
- Check both devices have ESP-NOW initialized
- Ensure devices are within range (~100m open space)

### Display not working
- Check I2C connections (SDA/SCL)
- Verify display address is 0x3C
- Try adjusting I2C pins in code if needed

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Silent Project**

- GitHub: [@silentprojectid](https://github.com/silentprojectid)
- Project: [AI-pocket](https://github.com/silentprojectid/AI-pocket)
- Instagram: [@sanzx_project.id](https://instagram.com/sanzx_project.id)

## 🙏 Acknowledgments

- Google Gemini AI for API access
- Adafruit for display libraries
- ESP32 community for support
- All contributors and testers

## 📸 Screenshots

*Add your device photos and screenshots here*

## 🔮 Future Plans

- [ ] Multiple language support
- [ ] Custom themes
- [ ] Extended battery analytics
- [ ] File system storage
- [ ] OTA updates
- [ ] More AI model options
- [ ] Game applications

## ⚠️ Disclaimer

This project is for educational purposes. Use Gemini API responsibly and within Google's terms of service. Battery monitoring values are estimates and may vary.

---

**Made with ❤️ by sanzx_project.id**

*Star ⭐ this repository if you find it useful!*

**Repository**: [github.com/silentprojectid/AI-pocket](https://github.com/silentprojectid/AI-pocket)
