# Open-Port-Discovery
### Identifying active network services and listening ports to analyze potential attack surfaces.

## Objective
The goal of this lab was to identify all "Listening" ports on a Windows machine. In cybersecurity, understanding which ports are open is critical for identifying the **Attack Surface**—the sum of all points where an unauthorized user can try to enter or extract data from an environment.

## Tools Used
* **PowerShell**: Utilizing the `Get-NetTCPConnection` cmdlet to query network statistics.

---

## Step-by-Step Procedure

### 1. Identifying Listening Ports
I ran a command to filter for TCP connections that are currently in a "Listen" state. This tells us which applications are waiting for an incoming connection.

```powershell
Get-NetTCPConnection | Where-Object {$_.State -eq "Listen"} | Select-Object LocalAddress, LocalPort, OwningProcess
```

<img width="1920" height="1040" alt="OPD_Screenshot" src="https://github.com/user-attachments/assets/7ce5e4b7-5aa2-48e0-b6d7-6b6b0947807a" />

---
## Reflection & Security Impact
This exercise ties directly into the **Network Artifacts** layer of the **Pyramid of Pain**. 

By monitoring these ports, I can:
1. **Detect Backdoors**: Spot unauthorized ports opened by malware.
2. **Attack Surface Reduction**: Identify unnecessary services that should be disabled to harden the system.
3. **Validate Services**: Ensure that only known, authorized applications are listening for traffic.
