# Cursor AI Installer for UNIX-like OS

Universal script for automatic installation of Cursor AI on popular unix-like platforms with some extensions and settings.

## 🚀 Features

- ✅ **Automatic system detection** - support for Linux (x64, arm64, arm) and macOS
- ✅ **Smart download** - automatic download of the latest version for your platform
- ✅ **Safe FUSE2 installation** - compatibility check with Ubuntu 24.04+
- ✅ **Built-in SVG icon** - creation of beautiful application icon
- ✅ **Interactive extension selection** - installation of popular extensions
- ✅ **Interface customization** - menu orientation selection (vertical/horizontal)
- ✅ **Memory Bank support** - automatic installation of cursor-memory-bank
- ✅ **Automatic updates** - easy update to the latest version
- ✅ **Comprehensive testing** - fully tested and validated
- ✅ **Error handling** - robust error handling with 14 exit points
- ✅ **Clean code** - well-structured, documented, and maintainable

## 📋 Supported Extensions

The script offers installation of the following extensions:

- **Remote Containers** - container development
- **Prettier** - code formatting
- **ESLint** - JavaScript/TypeScript linting
- **Gruvbox Theme** - dark theme
- **Material Icon Theme** - file icons
- **Symbols** - symbol icons and navigation ([marketplace](https://marketplace.cursorapi.com/items?itemName=castrogusttavo.symbols))
- **SQLTools** - database management

## 🛠️ Installation

### Requirements

- Linux (Ubuntu, Debian, etc.) or macOS
- sudo privileges
- Internet connection
- curl, wget, jq, figlet (installed automatically)

### Quick Start

```bash
# Download the script
wget https://raw.githubusercontent.com/your-repo/install_cursor_ai

# Make executable
chmod +x install_cursor_ai

# Run installation
./install_cursor_ai
```

### Alternative Installation

```bash
# Clone the repository
git clone https://github.com/your-repo/cursorall.git
cd cursorall

# Run the installer
./install_cursor_ai
```

## 📖 Usage

### Main Menu

```
------------------------
1. Install Cursor
2. Update Cursor
3. System Information
------------------------
```

### Options

1. **Install Cursor** - complete installation with extension selection
2. **Update Cursor** - update to the latest version
3. **System Information** - system diagnostics

### Usage Examples

#### Fresh Installation
```bash
./install_cursor_ai
# Output:
# Installing Cursor AI IDE..........
# (progress dots for a few seconds)
# ...
# Then interactive extension selection and menu orientation
```

#### System Check Only
```bash
echo "3" | ./install_cursor_ai
# Shows system information without installation
```

#### Update Existing Installation
```bash
./install_cursor_ai
# Select option 2
# Automatically updates to latest version
```

#### Non-Interactive Installation
```bash
# For automated installations (not recommended for first-time use)
yes | ./install_cursor_ai
```

## 🔧 Installation Process

### 1. System Detection
The script automatically detects:
- Operating system (Linux/macOS)
- Processor architecture (x64, arm64, arm)
- Forms the correct platform for download
- Validates system compatibility

### 2. FUSE2 Check
- Checks compatibility with Ubuntu 24.04+
- Safely installs FUSE2 only on compatible systems
- Adds user to fuse group
- Prevents system breakage on newer Ubuntu versions

### 3. Download and Installation
- Downloads the latest Cursor version for your platform
- Extracts AppImage to `/opt/cursor/`
- Creates SVG icon with proper XML structure
- Creates .desktop file for application menu
- Sets proper file permissions

### 4. Extensions and Settings
- Offers interactive extension selection (6 popular extensions)
- Allows menu orientation selection (vertical/horizontal)
- Installs Memory Bank (if available)
- Configures automatic settings and themes
- Creates extension recommendations file

## 🎨 Interface Settings

### Menu Orientation
- **Vertical menu** - recommended for wide screens
- **Horizontal menu** - standard orientation

### Automatic Settings
- Auto-formatting on save
- ESLint auto-fix
- Default themes and icons
- Symbol Icons enabled by default
- SQLTools and Remote Containers settings

## 🔒 Security

### Ubuntu 24.04+ Compatibility
The script automatically checks Ubuntu version and:
- Blocks FUSE2 installation on Ubuntu 24.04+ (prevents system breakage)
- Warns about potential issues
- Offers alternative solutions
- Maintains system stability

### Access Rights
- Minimal sudo usage (only when necessary)
- Safe directory creation with proper permissions
- Proper file permissions for security
- Cleanup of temporary files after installation

### Error Handling
- 14 comprehensive exit points for different error scenarios
- Graceful error messages with clear instructions
- Automatic cleanup on failure
- Validation of all critical operations

## 🐛 Troubleshooting

### Download Issues
```bash
# Check internet connection
ping -c 3 google.com

# Check API availability
curl -I https://www.cursor.com/api/download

# Test Cursor API response
curl -sL "https://www.cursor.com/api/download?platform=linux-x64&releaseTrack=stable"
```

### Permission Issues
```bash
# Check sudo privileges
sudo -l

# Fix script permissions
chmod +x install_cursor_ai

# Check directory permissions
ls -ld /opt/ /usr/share/applications/
```

### FUSE2 Issues
```bash
# Check Ubuntu version
cat /etc/os-release

# Check FUSE2 availability
which fusermount

# Check FUSE device
ls -la /dev/fuse
```

### Script Issues
```bash
# Check script syntax
bash -n install_cursor_ai

# Check script permissions
ls -la install_cursor_ai

# Run with debug output
bash -x install_cursor_ai
```

## ⚠️ Known Issues & Solutions

### Ubuntu 24.04+ FUSE2 Limitation
**Issue:** FUSE2 installation is blocked on Ubuntu 24.04+ for safety  
**Solution:** This is intentional behavior to prevent system breakage. AppImage will run without FUSE2 (may be slower but safe)

### Network Connectivity Issues
**Issue:** Script fails to download Cursor  
**Solution:** 
- Check internet connection
- Verify firewall settings
- Try using a VPN if region-restricted

### Permission Denied Errors
**Issue:** Script cannot write to system directories  
**Solution:**
- Ensure sudo privileges
- Check directory permissions
- Run with proper user permissions

### Extension Installation Failures
**Issue:** Extensions not installing properly  
**Solution:**
- Check available disk space
- Verify extension directory permissions
- Re-run installation process

## 📁 Installation Structure

```
/opt/cursor/
├── AppRun                    # Executable file
├── cursor-logo.svg          # Application icon
├── resources/
│   └── app/
│       ├── extensions/      # Installed extensions
│       │   ├── cursor-memory-bank/    # Memory Bank extension
│       │   ├── anysphere.remote-containers/
│       │   ├── esbenp.prettier-vscode/
│       │   ├── dbaeumer.vscode-eslint/
│       │   ├── jdinhlife.gruvbox/
│       │   ├── PKief.material-icon-theme/
│       │   ├── castrogusttavo.symbols/
│       │   └── mtxr.sqltools/
│       └── user-data/       # User data
│           └── User/
│               ├── settings.json      # User settings
│               └── extensions.json    # Extension recommendations
└── ...

/usr/share/applications/
└── cursor.desktop          # Applications menu entry
```

## 🔧 Technical Details

### Script Specifications
- **Language:** Bash
- **Size:** 559 lines
- **Functions:** 10
- **Exit Points:** 14
- **Dependencies:** curl, wget, jq, figlet
- **Supported Platforms:** Linux (x64, arm64, arm), macOS
- **Extensions:** 7 available extensions including Symbols

### API Integration
- **Endpoint:** https://www.cursor.com/api/download
- **Parameters:** platform, releaseTrack
- **Response Format:** JSON
- **User-Agent:** Chrome-compatible for compatibility

### File Operations
- **Installation Directory:** `/opt/cursor/`
- **Icon Path:** `/opt/cursor/cursor-logo.svg`
- **Desktop Entry:** `/usr/share/applications/cursor.desktop`
- **Temporary Files:** `/tmp/` (auto-cleaned)

## 🔄 Updates

To update Cursor:
1. Run the script
2. Select option "2. Update Cursor"
3. The script will automatically:
   - Download the new version
   - Update files
   - Reinstall extensions and settings
   - Preserve user configurations
   - Clean up old files

### Update Process Details
- **Safe Update:** Preserves existing configurations and extensions
- **Clean Installation:** Removes old files before installing new version
- **Extension Reinstallation:** Reinstalls all previously selected extensions
- **Settings Preservation:** Maintains user preferences and themes

## 🧪 Testing

The script has been thoroughly tested and validated:

### Test Coverage
- ✅ **Syntax Validation** - No syntax errors
- ✅ **Menu System** - All options work correctly
- ✅ **System Detection** - Proper OS and architecture detection
- ✅ **Dependencies** - All required tools available
- ✅ **FUSE2 Compatibility** - Safe handling of Ubuntu 24.04+
- ✅ **API Integration** - Successful Cursor API connectivity
- ✅ **Error Handling** - 14 comprehensive exit points
- ✅ **File Operations** - Proper file and directory management
- ✅ **Progress Bar** - Compact progress dots animation instead of ASCII-art

### Test Environment
- **OS:** Ubuntu 24.04.2 LTS
- **Architecture:** x86_64
- **Kernel:** 6.11.0-29-generic
- **Test Date:** July 2, 2024

For detailed test results, see [TESTING_REPORT.md](TESTING_REPORT.md).

## 🤝 Contributing

1. Fork the repository
2. Create a branch for new feature
3. Make changes
4. Run tests to ensure functionality
5. Create Pull Request

### Development Guidelines
- Follow existing code structure
- Add proper error handling
- Test on multiple platforms
- Update documentation
- Maintain backward compatibility

## 📄 License

MIT License - see LICENSE file for details.

## 📋 Version History

### v1.0 (July 2, 2024)
- ✅ Initial release with full English translation
- ✅ Comprehensive system detection and compatibility
- ✅ Interactive extension selection (7 extensions)
- ✅ Menu orientation customization
- ✅ Memory Bank integration
- ✅ Ubuntu 24.04+ safety features
- ✅ Complete testing and validation
- ✅ Comprehensive error handling (14 exit points)
- ✅ Automatic cleanup and file management
- ✅ Symbols extension with default icon settings

### Planned Features
- 🔄 Configuration backup and restore
- 🔄 Uninstall functionality
- 🔄 Silent installation mode

## 🆘 Support

If you encounter issues:
1. Check the "Troubleshooting" section
2. Review the testing report
3. Check known issues and solutions
4. Create an Issue in the repository
5. Describe your system and the problem
6. Include error messages and logs

## 📞 Contact

- **Repository:** [GitHub Repository](https://github.com/your-repo/cursorall)
- **Issues:** [GitHub Issues](https://github.com/your-repo/cursorall/issues)
- **Documentation:** [TESTING_REPORT.md](TESTING_REPORT.md)

---

## 🙏 Acknowledgments

### Cursor AI Team
Special thanks to the **Cursor AI** development team for creating an amazing AI-powered code editor that revolutionizes the development experience.

- **Cursor AI**: [cursor.com](https://cursor.com)
- **GitHub**: [github.com/getcursor/cursor](https://github.com/getcursor/cursor)

### Extension Developers
Grateful appreciation to the developers of the extensions included in this installer:

- **Remote Containers**: [Anysphere](https://github.com/anysphere) - Container development support
- **Prettier**: [Prettier Team](https://github.com/prettier/prettier) - Code formatting
- **ESLint**: [ESLint Team](https://github.com/eslint/eslint) - JavaScript/TypeScript linting
- **Gruvbox Theme**: [Jinhlife](https://github.com/jinhlife) - Beautiful dark theme
- **Material Icon Theme**: [Philipp Kief](https://github.com/PKief) - File and folder icons
- **Symbols**: [Gustavo Castro](https://github.com/castrogusttavo) - Symbol icons and navigation
- **SQLTools**: [Matheus Teixeira](https://github.com/mtxr) - Database management

### Memory Bank
Thanks to [vanzan01](https://github.com/vanzan01) for the excellent **Cursor Memory Bank** system that enhances the development workflow.

---

**Made with ❤️ for the Cursor AI community** 