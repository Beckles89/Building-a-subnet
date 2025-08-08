# Building-a-subnet

---

## 🔧 Project Overview: Creating a Subnet in VirtualBox

This project demonstrates how to **create and configure a subnet** using **VirtualBox** and **virtual machines (VMs)**. It walks through setting up internal networking, assigning static IPs, testing connectivity, and understanding basic network segmentation.

---

### 🗂 GitHub Repository Structure

```
virtualbox-subnet-setup/
├── README.md
├── images/
│   ├── vm-settings.png
│   ├── network-settings.png
│   └── ping-test.png
├── VM_Config_Guide.md
├── Subnet_Troubleshooting.md
├── Skills_Learned.md
└── LICENSE
```

---

## 📄 README.md

Here is the content for the `README.md`:

---

# 🧩 Creating a Subnet in VirtualBox with VMs

## 📌 Project Goal

To simulate a subnet in a virtualized environment using VirtualBox and multiple VMs (Ubuntu, Kali Linux, or Windows), and understand how subnetting works in real-world network segmentation.

---

## 🛠 Requirements

* Oracle VirtualBox (latest version)
* At least 2 virtual machines (preferably Ubuntu/Kali)
* Basic networking knowledge (IP addressing, subnetting)

---

## 🌐 Steps to Create a Subnet in VirtualBox

### 1. Create VMs

* Launch VirtualBox and create 2+ VMs (Linux or Windows).
* Use the same operating system for simplicity (e.g., Ubuntu Desktop).

### 2. Configure Network Settings

* Go to each VM’s **Settings > Network** tab.
* **Adapter 1**:

  * Attach to: `Internal Network`
  * Name: `SubnetLab`

> This ensures all selected VMs share a private LAN-like network.

### 3. Boot the VMs

* Start each VM and log in.

### 4. Assign Static IP Addresses

#### Example for Ubuntu VM:

Edit `/etc/netplan/01-netcfg.yaml` (may vary based on your Linux distro):

```yaml
network:
  version: 2
  ethernets:
    enp0s3:
      addresses: [192.168.10.10/24]
      gateway4: 192.168.10.1
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
```

Run:

```bash
sudo netplan apply
```

Repeat with different IPs for each VM (e.g., 192.168.10.11, 192.168.10.12).

### 5. Test Connectivity

* Use the `ping` command to verify subnet communication:

```bash
ping 192.168.10.11
```

* All VMs should be able to ping each other if the subnet is correctly configured.

---

## 🧠 Skills Learned

See [Skills\_Learned.md](Skills_Learned.md) for a detailed breakdown.

---

## ❗ Troubleshooting

See [Subnet\_Troubleshooting.md](Subnet_Troubleshooting.md)


---

## 🔗 Useful Resources

* [Netplan Configuration Guide](https://netplan.io/examples)
* [Oracle VirtualBox Networking Docs](https://www.virtualbox.org/manual/ch06.html)

---

## 🧠 Skills\_Learned.md

```
# Skills Learned During the Subnet Project

1. **Networking Fundamentals**
   - Subnetting, IP addressing, CIDR notation
   - Understanding broadcast domains and gateways

2. **VirtualBox Configuration**
   - Setting up internal networks
   - Bridging, NAT, and internal adapter types

3. **Linux Networking**
   - Editing and applying static IP configuration
   - Netplan usage on Ubuntu-based systems

4. **Troubleshooting Skills**
   - Diagnosing ping issues (firewall, misconfiguration)
   - Understanding ARP tables and routing

5. **Testing and Validation**
   - Verifying connectivity
   - Using tools like `ping`, `ifconfig`, and `ip a`

6. **Documentation**
   - Creating a structured GitHub project
   - Writing step-by-step technical instructions
```
