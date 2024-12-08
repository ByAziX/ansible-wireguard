# Ansible Playbook for WireGuard VPN Configuration and Reset

This README explains how to configure and reset a WireGuard VPN using the provided Ansible playbooks.

---

## Setup Instructions

1. **Update the `hosts` file**:

- Open the `hosts` file and replace the example IPs with your own server details. Example:

```ini
[wireguard]
YOUR_SERVER_NAME ansible_host=YOUR_SERVER_IP ansible_user=root private_ip=10.0.0.1
YOUR_SERVER_NAME ansible_host=YOUR_SERVER_IP ansible_user=root private_ip=10.0.0.2
```

2. **Add SSH host keys to `known_hosts`**:

- Use the following command to automatically add SSH host keys for all servers to your `~/.ssh/known_hosts` file:
```bash
ansible-playbook -i hosts add_known_hosts.yml --ask-pass
```

3. **Run the playbook to configure WireGuard**:

```bash
ansible-playbook -i hosts wireguard.yml --ask-pass
```

4. **Test the connection**:

SSH into one of the servers and ping another server's private IP:

```bash
ssh root@<public_ip>
ping <private_ip>
```

5. **To reset WireGuard configuration**:

```bash
ansible-playbook -i hosts reset_wireguard.yml --ask-pass
```
