---

# 📂 Wazuh SIEM Deployment - Phase 3: File Integrity Monitoring (FIM)

This phase covers the configuration and deployment of File Integrity Monitoring (FIM) rules targeting critical asset directories on the remote host. Real-time scanning boundaries were set up to watch for illegal additions, deletions, or structural modifications to web root elements.

## 🚀 Deployment Steps & Execution

### 1. FIM Configuration Matrix Setup
The local `<syscheck>` subsystem architecture block within the Windows endpoint's agent configuration (`ossec.conf`) was modified to track directory mutations dynamically using cryptographic hash tracking and real-time monitoring flags.

```xml
<!-- File Location: C:\Program Files (x86)\ossec-agent\ossec.conf -->
<!-- Embedded inside the core <syscheck> structure -->
<directories check_all="yes" realtime="yes">C:\inetpub\wwwroot\internee_critical_assets</directories>

# Drop a new mock operational script asset (Triggers Rule 554)
New-Item -Path "C:\inetpub\wwwroot\internee_critical_assets\database_config.php" -ItemType "file" -Value "<?php echo 'Database Connected'; ?>"

# Execute an unauthorized structural text mutation (Triggers Rule 550)
Add-Content -Path "C:\inetpub\wwwroot\internee_critical_assets\database_config.php" -Value " // Admin access enabled."

