# rConfig SNMP Trap Registry

An official registry of SNMP trap definitions for rConfig V8+ users. This registry provides pre-defined trap filters for common network events like configuration changes, interface state changes, system restarts, and environmental alerts.

## 📋 Overview

This repository contains JSON files with SNMP trap definitions that rConfig V8+ users can download to quickly set up trap filtering for their network devices. Instead of manually creating trap filters for common events, users can sync this registry to get:

- **Pre-configured filters** for common network events (config changes, link up/down, restarts)
- **Vendor-specific traps** for Cisco, Juniper, Fortinet, and other major vendors  
- **Standardized categorization** with appropriate severity levels
- **Ready-to-use OIDs** with human-readable descriptions

## 🎯 For rConfig Users

This registry eliminates the need to manually research and configure trap filters for common network events. Common use cases include:

- **Configuration Change Monitoring**: Automatically detect when device configs are modified
- **Interface Monitoring**: Track link up/down events across your network
- **System Health**: Monitor device restarts, CPU/memory alerts, environmental conditions
- **Security Events**: Detect authentication failures and security-related traps

## 🗂️ Repository Structure

```
├── standard.json       # RFC standard SNMP traps
├── cisco.json         # Cisco Systems trap definitions
├── juniper.json       # Juniper Networks trap definitions
├── fortinet.json      # Fortinet trap definitions
└── vendors.json       # Vendor metadata and enterprise OIDs
```

## 🤝 Contributing

We welcome contributions from the rConfig community and network engineers! 

### Adding New Traps

1. Fork this repository
2. Add trap definitions to the appropriate vendor file
3. Follow the existing JSON structure and validation rules
4. Test with the validation scripts in `/tools`
5. Submit a pull request with clear descriptions

### Contribution Guidelines

- **Accurate Information**: Ensure trap OIDs and descriptions are correct
- **Complete Details**: Include name, category, severity, description, and MIB when available
- **Real-world Testing**: Verify traps work with actual devices when possible
- **Documentation**: Update this README if adding new vendors or categories

### Vendor Support

Currently supported vendors:
- ✅ Standard SNMP (RFC traps)
- ✅ Cisco Systems
- ✅ Juniper Networks  
- ✅ Fortinet
- 🔄 HPE/Aruba (in progress)
- 🔄 MikroTik (in progress)

Want to add a vendor? Create an issue or submit a PR!

## 🐛 Issues & Support

### Bug Reports
If you find incorrect trap information or issues with the registry:

1. Check existing [issues](https://github.com/rconfig/snmp-trap-registry/issues)
2. Create a new issue with:
   - Vendor and device model
   - Expected vs actual trap behavior  
   - MIB references if available
   - rConfig version

### Feature Requests
Request new vendors, trap categories, or registry features via GitHub issues.

### rConfig Support
For rConfig-specific questions:
- [rConfig Documentation](https://docs.rconfig.com)
- [rConfig Community Forum](https://community.rconfig.com)
- [rConfig GitHub](https://github.com/rconfig/rconfig)

## 📄 License

This registry is provided under the MIT License. See [LICENSE](LICENSE) for details.

## 🏷️ Versioning

Registry files use semantic versioning:
- **Major**: Breaking changes to JSON structure
- **Minor**: New vendors or significant trap additions
- **Patch**: Bug fixes, small additions, description updates

Current version: `v1.0.0`

## 🔗 Links

- [rConfig Official Site](https://www.rconfig.com)
- [rConfig V8 Documentation](https://docs.rconfig.com/v8)
- [SNMP Trap Filtering Guide](https://docs.rconfig.com/v8/snmp-traps)
- [Community Forum](https://community.rconfig.com)

---

**Made with ❤️ for the rConfig community**

## 🚀 Usage in rConfig

### Recommended: In-App Import (Easiest Method)

The best way to use this registry is through rConfig's built-in import feature:

1. **Navigate to SNMP Trap Filters** page in your rConfig V8+ installation
2. **Click the "Import Registry" button** to download the latest trap definitions
3. **Create a new filter** and you'll see enhanced autocomplete with pre-defined traps
4. **Select from available options** - trap details will auto-populate (name, description, severity, category)

### Offline/Manual Installation

If your rConfig server doesn't have internet access:

1. **Download JSON files** from this repository to your local machine
2. **Upload to server** and place files in: `storage/app/rconfig/snmp_traps/`
3. **Clear cache** (if needed): `php artisan snmp:registry clear`
4. **Refresh the SNMP Trap Filters page** to see the new options

### Command Line Options

**Check Registry Status:**
```bash
php artisan snmp:registry status
```

**Download Latest Registry:**
```bash
php artisan snmp:registry download
```

**Force Update (Overwrite Recent Files):**
```bash
php artisan snmp:registry download --force
```

### Enhanced Trap Filtering Experience

Once the registry is imported, creating SNMP trap filters becomes much easier:

1. **Smart Autocomplete**: Start typing a trap name or OID to see matching suggestions
2. **Auto-populated Fields**: Select a trap and rConfig automatically fills in:
   - Trap name and description
   - Severity level (info/warning/error/critical)
   - Category (configuration/interface/system/etc.)
   - Associated MIB information
3. **Vendor Filtering**: Filter available traps by vendor (Cisco, Juniper, Fortinet, etc.)
4. **Quick Setup**: Get monitoring for common events in seconds rather than hours

### Common Filter Examples

After importing the registry, you can quickly create filters for:

- **Configuration Monitoring**: 
  - Cisco Config Change (`1.3.6.1.4.1.9.9.43.2.0.1`)
  - Juniper Config Change (`1.3.6.1.4.1.2636.4.6.0.1`)
  - Fortinet Config Change (`1.3.6.1.4.1.12356.101.6.0.701`)

- **Interface Monitoring**:
  - Standard Link Down (`1.3.6.1.6.3.1.1.5.3`)
  - Standard Link Up (`1.3.6.1.6.3.1.1.5.4`)

- **System Health**:
  - System Cold Start (`1.3.6.1.6.3.1.1.5.1`)
  - Cisco CPU High (`1.3.6.1.4.1.9.9.109.2.0.1`)
  - Fortinet HA Failover (`1.3.6.1.4.1.12356.101.6.0.303`)

- **Security Events**:
  - Authentication Failure (`1.3.6.1.6.3.1.1.5.5`)
  - Fortinet IPS Alert (`1.3.6.1.4.1.12356.101.6.0.101`)

### Raw File Access

Files are available via GitHub's CDN for direct download:

```
https://raw.githubusercontent.com/
