# Wazuh-EndPoint-Security-and-Monitoring
# Wazuh SIEM Deployment - Phase 1: Server Architecture

This repository documents the deployment and configuration of an enterprise-grade Wazuh SIEM (Security Information and Event Management) instance on a dedicated Linux host. 

---

## 🏗️ System Topology & Architecture

The initial phase consists of an **All-in-One (AIO) Single-Node Deployment**. The central manager, indexer, and dashboard web interface are co-located on a single host.
### Host Environment Configurations
* **OS:** Kali Linux x86_64
* **Hostname:** `buffer`
* **Internal Network Interfaces:**
  * `eth0`: `192.168.124.23/24`
  * `wlan0` (Management IP): `192.168.0.13/24`

---

## 🚀 Deployment Script & Execution

The stack was deployed using the automated Wazuh installation assistant to provision certificates, configure internal security boundaries, and initialize the system components.

### Automated Installation Command
```bash
# Executed as root to install all components on a single host (-a) 
# and optimize configuration parameters (-o)
sudo bash ./wazuh-install.sh -a -o
---
## Varification Status
## sudo systemctl status wazuh-managern

● wazuh-manager.service - Wazuh manager

     Loaded: loaded (/usr/lib/systemd/system/wazuh-manager.service; enabled; preset: disabled)

     Active: active (running) since Tue 2026-06-30 04:38:16 EDT; 57min ago

 Invocation: 2bd4bf9d0c1a418cbdc069526ba3c2df

      Tasks: 211 (limit: 9281)

     Memory: 1.4G (peak: 2.6G)

        CPU: 18min 30.275s

     CGroup: /system.slice/wazuh-manager.service

             ├─83412 /var/ossec/framework/python/bin/python3 /var/ossec/api/scripts/wazuh_apid.py

             ├─83413 /var/ossec/framework/python/bin/python3 /var/ossec/api/scripts/wazuh_apid.py

             ├─83414 /var/ossec/framework/python/bin/python3 /var/ossec/api/scripts/wazuh_apid.py

             ├─83417 /var/ossec/framework/python/bin/python3 /var/ossec/api/scripts/wazuh_apid.py

             ├─83420 /var/ossec/framework/python/bin/python3 /var/ossec/api/scripts/wazuh_apid.py

             ├─83461 /var/ossec/bin/wazuh-authd

             ├─83473 /var/ossec/bin/wazuh-db

             ├─83516 /var/ossec/bin/wazuh-execd

             ├─83527 /var/ossec/bin/wazuh-analysisd

             ├─83544 /var/ossec/bin/wazuh-syscheckd

             ├─83558 /var/ossec/bin/wazuh-remoted

             ├─83601 /var/ossec/bin/wazuh-logcollector

             ├─83660 /var/ossec/bin/wazuh-monitord

             └─83680 /var/ossec/bin/wazuh-modulesd



Jun 30 04:38:10 buffer env[83301]: Started wazuh-syscheckd...

Jun 30 04:38:11 buffer env[83301]: Started wazuh-remoted...

Jun 30 04:38:12 buffer env[83301]: Started wazuh-logcollector...

Jun 30 04:38:13 buffer env[83301]: Started wazuh-monitord...

Jun 30 04:38:13 buffer env[83677]: 2026/06/30 04:38:13 wazuh-modulesd:router: INFO: Loaded router module.

Jun 30 04:38:13 buffer env[83677]: 2026/06/30 04:38:13 wazuh-modulesd:content_manager: INFO: Loaded content_manager module.

Jun 30 04:38:13 buffer env[83677]: 2026/06/30 04:38:13 wazuh-modulesd:inventory-harvester: INFO: Loaded Inventory harvester module.

Jun 30 04:38:14 buffer env[83301]: Started wazuh-modulesd...

Jun 30 04:38:16 buffer env[83301]: Completed.

Jun 30 04:38:16 buffer systemd[1]: Started wazuh-manager.service - Wazuh manager. 
