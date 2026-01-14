# Day 13 – Azure Learning Journey

## Objective
The objective of Day 13 was to enable secure, password-less SSH access to an Azure Virtual Machine as the **root** user by manually adding an SSH public key from the Azure client (landing host) to the VM.

---

## Azure Services / Concepts Covered
- Azure Virtual Machines (Linux)
- SSH key-based authentication
- Azure cloud-init configuration
- Linux SSH daemon (`sshd`)
- Root user access control
- SSH host key verification

---

## Steps I Took

1. Logged into the Azure Portal and confirmed the VM **datacenter-vm** was running in the **West US** region.
2. Copied the VM’s Public IP address from the Azure Portal.
3. From the Azure client host, connected to the VM using the default user:

```bash
   ssh azureuser@<VM_PUBLIC_IP>
````

4. Switched to the root user on the VM:

   ```bash
   sudo -i
   ```
5. Created the root SSH directory and set correct permissions:

   ```bash
   mkdir -p /root/.ssh
   chmod 700 /root/.ssh
   ```
6. On the Azure client host, retrieved the root public SSH key:

   ```bash
   cat /root/.ssh/id_rsa.pub
   ```
7. Added the copied public key to the VM’s root `authorized_keys` file:

   ```bash
   echo "<public-key>" >> /root/.ssh/authorized_keys
   ```
8. Fixed file permissions and ownership:

   ```bash
   chmod 600 /root/.ssh/authorized_keys
   chown -R root:root /root/.ssh
   ```
9. Updated SSH configuration to allow root login:

   * Edited `/etc/ssh/sshd_config` and ensured:

     ```
     PermitRootLogin yes
     PubkeyAuthentication yes
     PasswordAuthentication no
     ```
10. Disabled Azure’s default root restriction by editing cloud-init configuration:

    * Edited `/etc/cloud/cloud.cfg` and changed:

      ```
      disable_root: true
      ```

      to:

      ```
      disable_root: false
      ```
11. Cleaned cloud-init state and restarted services:

    ```bash
    cloud-init clean
    systemctl restart sshd
    reboot
    ```
12. On the Azure client host, resolved SSH host key mismatch caused by reboot:

    ```bash
    ssh-keygen -f "/root/.ssh/known_hosts" -R "<VM_PUBLIC_IP>"
    ```
13. Verified password-less root SSH access **from the Azure client host**:

    ```bash
    ssh root@<VM_PUBLIC_IP>
    ```

---

## Issues Faced and How They Were Resolved

* **Root SSH login initially blocked**
  Azure’s cloud-init configuration explicitly disables root login by default. This was resolved by updating `disable_root` in `/etc/cloud/cloud.cfg`.

* **SSH tests failing when run from inside the VM**
  SSH authentication depends on the client’s private key. The correct verification had to be done from the **Azure client host**, not from inside the VM.

* **“Remote host identification has changed” warning**
  Occurred after rebooting the VM. Resolved by removing the old host key from `known_hosts`.

---

## Key Takeaways

* Azure Linux VMs enforce additional security through **cloud-init**, not just `sshd_config`.
* Root SSH access is disabled by default and must be explicitly enabled.
* SSH authentication always uses the **client’s private key**.
* SSH host key warnings are common after VM reboots and are resolved via `known_hosts`.
* Understanding both Linux internals and cloud provider defaults is critical for real-world DevOps work.

---

## Conclusion

Day 13 was an advanced Azure and Linux security task that involved configuring root-level SSH access in a controlled and secure manner. It reinforced deep concepts around SSH, cloud-init, Azure VM security defaults, and real-world troubleshooting practices commonly encountered by DevOps engineers.
