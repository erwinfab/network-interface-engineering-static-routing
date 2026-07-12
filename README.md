# Red Hat Enterprise Linux (RHEL 9.3) Core Competency: Enterprise Network Architecture & Local Resolution Management

## 🎯Project Overview
This project validates administrative competencies in enterprise Network Interface Card (NIC) provisioning, multi-homed static IPv4 routing assignments, persistent host identification mapping, and local canonical hostname resolution within Red Hat Enterprise Linux 9.3. The objective is to construct a hardened, predictable runtime network environment by deploying localized profile parameters via the NetworkManager subsystem without reliance on dynamic address leases.

## 💻Environments and Technologies Used
Operating System Environment: Red Hat Enterprise Linux 9.3 (RHEL)

Core Utilities Demanded: NetworkManager CLI (`nmcli`), `hostnamectl`, `/etc/hosts` configuration engine, local system console bridges

## 📋Objectives and Scenario
The scenario models a production infrastructure reconfiguration sequence where a server node must transition from dynamic address routing over to a dual-homed, statically assigned administrative interface profile while maintaining secondary address blocks and handling specific local lookups.

### Technical Specification Requirements:
**Interface Discovery**: Programmatically audit active Ethernet controllers to isolate physical interface handles and corresponding runtime profile tags. 


**Static Interface Engineering**: Construct and activate a target network profile named `static` configured to bypass DHCP layers completely. 


**Primary IP Routing Topography**: Apply static parameters mapping an IPv4 address of `172.25.250.111/24`, gateway routing to `172.25.250.254`, and upstream DNS resolution targeting `172.25.250.254`. 


**Multi-Homed Addressing Expansion**: Inject a secondary alias IPv4 address block of `172.25.250.211/24` onto the same static interface context without overriding the primary network attachment.  


**Persistent Naming Configuration**: Enforce a fully qualified domain name (FQDN) system change altering the system node identifier to `server-review4.lab4.example.com.`  


**Canonical Local Name Resolution**: Adjust local name mapping systems to establish `client-review4` as the canonical local lookup tag resolving immediately to servera's destination address (`172.25.250.10`).


**Environment Profile Rollback**: Re-activate the primary pre-existing connection framework profile to clean down custom interface routes back to target infrastructure configurations.

## 🛠️ High-Level Deployment and Configuration Steps

**Step 1: Interface Diagnostics & Primary Static Provisioning**
Audit the NetworkManager engine state variables via the machine console context to map active profiles and initialize the hardened network configuration structure.  

* Query active network connection properties and device interface labels
   * `nmcli connection show`
   * `nmcli device status`

<img width="702" height="426" alt="image" src="https://github.com/user-attachments/assets/9492dba9-762d-400a-b99f-0bb0024ee722" />


* Add a clean static connection profile bound to the discovered device interface as root
   * `nmcli connection add type ethernet con-name static ifname <INTERFACE_NAME> ipv4.addresses 172.25.250.111/24 ipv4.gateway 172.25.250.254 ipv4.dns 172.25.250.254 ipv4.method manual`

<img width="1038" height="135" alt="image" src="https://github.com/user-attachments/assets/f9113853-3bfd-4113-b315-418f1dbeaf28" />


**Step 2: Multi-Homed Routing Expansion & SSH Connection Cutover**
Append the secondary administrative IP mapping block onto the target workspace profile configuration array.  

* Append a secondary alias IPv4 target block without disturbing the existing matrix
   * `nmcli connection modify static +ipv4.addresses 172.25.250.211/24`


⚠️ Critical Infrastructure Alert (SSH Session Freeze):Executing `nmcli connection up static` over a remote network shell immediately drops the active dynamic DHCP routing parameters (lab/Wired connection 1) to load the new static parameters. Because the active SSH connection relies on the old IP routing path, the remote terminal window instantly loses its route and freezes.  To resolve this lockout without resetting the node, administrators must shift away from network-dependent streams and attach directly to the system via the local graphical hypervisor console bridge (`virt-manager`). 

* Force connection profile activation securely inside the local server console
   * `nmcli connection up static`

<img width="940" height="340" alt="image" src="https://github.com/user-attachments/assets/d0f6200d-37ad-428a-95ca-aab0dd94ca38" />


**Step 3: Enterprise Naming Realignment & Local Host Mapping**

<img width="886" height="761" alt="image" src="https://github.com/user-attachments/assets/07c7b927-d476-41cf-8af7-4db94b1fdfa6" />


**Step 4:**


## 📊 Verification and Testing

**Step 1: Laboratory Compliance Execution**
Return to your virtual workstation context terminal and trigger the programmatic laboratory script to evaluate runtime infrastructure setup checks.

<img width="691" height="439" alt="image" src="https://github.com/user-attachments/assets/e726d815-ce49-48dd-8a43-65c6962f56d4" />


**Step 2: Sandbox Environment Teardown**
De-provision local tracking mechanisms to return the deployment sandbox back to baseline conditions.

<img width="763" height="190" alt="image" src="https://github.com/user-attachments/assets/886f6069-0670-477c-b8cf-14cd9028f8b8" />

