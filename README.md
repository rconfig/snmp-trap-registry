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

### Downloading the Registry

**Option 1: Automatic Download (Recommended)**
```bash
# From rConfig console
php artisan snmp:registry download

# Check status
php artisan snmp:registry status

# Force update
php artisan snmp:registry download --force
```

**Option 2: Manual Download**
1. Download JSON files from this repository
2. Place them in `storage/app/rconfig/snmp_traps/` directory
3. Clear cache: `php artisan snmp:registry clear`

### Using Trap Filters

Once downloaded, the registry enhances your rConfig SNMP trap filtering:

1. **Enhanced Autocomplete**: When creating trap filters, start typing to see suggestions
2. **Pre-filled Information**: Select a trap to auto-populate description, severity, and category
3. **Vendor Filtering**: Filter available traps by vendor in the UI
4. **Quick Setup**: Common traps like "Cisco Config Change" are ready to use

### Example Common Filters

After downloading the registry, you can quickly create filters for:

- **Cisco Configuration Changes**: `1.3.6.1.4.1.9.9.43.2.0.1`
- **Interface Link Down**: `1.3.6.1.6.3.1.1.5.3`
- **Interface Link Up**: `1.3.6.1.6.3.1.1.5.4`
- **System Cold Start**: `1.3.6.1.6.3.1.1.5.1`
- **Authentication Failure**: `1.3.6.1.6.3.1.1.5.5`

### Raw File Access

Files are available via GitHub's CDN for direct download:

```
https://raw.githubusercontent.com/
