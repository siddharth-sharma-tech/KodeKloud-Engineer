# Task 16: Firewall Configuration

## 1. Problem Statement

The Nautilus system administrators team has rolled out a web UI application for their backup utility on the Nautilus application server 1 within the Stratos Datacenter. This application runs on port 3002and appropriate firewall rules must be configured to allow incoming traffic. To achieve this, firewalld needs to be installed and configured on the application server. To ensure proper functionality, the following requirements have been identified:



Install and enable the firewalld service.
Allow all incoming connections on port 3002/tcp.
Ensure the zone is set to public.

## 2. Tools & Technologies Used

- Linux
- Firewalld
- Yum package manager
- systemd
- SSH

## 3. Implementation Steps

### Step 1: Connect to App Server 1

From the Jump Host, connect using the SSH username `tony`:

```bash
ssh tony@stapp01
```

### Step 2: Install Firewalld

Install firewalld using `yum`:

```bash
sudo yum install -y firewalld
```

### Step 3: Enable and Start Firewalld

Enable the service and start it immediately:

```bash
sudo systemctl enable --now firewalld
```

Verify the service:

```bash
sudo systemctl status firewalld
```

### Step 4: Set the Default Zone to Public

Set the default firewall zone to `public`:

```bash
sudo firewall-cmd --set-default-zone=public
```

Verify the default zone:

```bash
sudo firewall-cmd --get-default-zone
```

Expected output:

```text
public
```

### Step 5: Allow Incoming Traffic on Port 3002

Run the following command to permanently allow incoming TCP traffic on port `3002` in the `public` zone:

```bash
sudo firewall-cmd --zone=public --add-port=3002/tcp --permanent
```

### Step 6: Reload Firewalld

Apply the permanent firewall rule:

```bash
sudo firewall-cmd --reload
```

### Step 7: Verify the Configuration

Check the default zone:

```bash
sudo firewall-cmd --get-default-zone
```

Check the allowed ports in the public zone:

```bash
sudo firewall-cmd --zone=public --list-ports
```

Expected output should include:

```text
3002/tcp
```

Check the firewall service:

```bash
sudo systemctl status firewalld
```

## 4. Commands Used

| Command | Purpose |
|---|---|
| `sudo yum install -y firewalld` | Installs the firewalld package |
| `sudo systemctl enable --now firewalld` | Enables and starts firewalld |
| `sudo firewall-cmd --set-default-zone=public` | Sets the default firewall zone |
| `sudo firewall-cmd --zone=public --add-port=3002/tcp --permanent` | Permanently allows TCP port 3002 in the public zone |
| `sudo firewall-cmd --reload` | Applies permanent firewall changes |
| `sudo firewall-cmd --get-default-zone` | Displays the default zone |
| `sudo firewall-cmd --zone=public --list-ports` | Displays allowed ports in the public zone |
| `sudo systemctl status firewalld` | Checks the firewall service status |

## 5. Final Result

The expected configuration on App Server 1:

- Firewalld installed using `yum`.
- Firewalld enabled and running.
- Default firewall zone set to `public`.
- Incoming TCP traffic allowed on port `3002`.
- Firewall rule saved permanently.

## 6. What I Learned

- How to install firewalld using the `yum` package manager.
- How to enable and start a Linux service using systemd.
- How to set the default firewall zone.
- How to allow incoming traffic on a specific TCP port.
- How to create permanent firewall rules.
- How to verify firewall configuration.

## 7. Real-World Use Case in IT Companies

In real IT environments, web applications and internal tools listen on specific ports.

For example, the backup utility web interface uses port `3002`. The Linux administrator must configure the server firewall to allow incoming connections on that port.

This allows authorized users and systems to access the application while keeping other ports protected.

Opening the port alone does not guarantee access. The application must be running and listening on port `3002`, and any external firewall or cloud security group must also allow the traffic.

## 8. Practical Experience

- **Learning Platform:** KodeKloud
- **Category:** Linux Administration
- **Topic:** Firewalld Configuration and Port Management
- **Difficulty:** Beginner
- **Evidence:** Terminal screenshots showing the connection to App Server 1, firewalld installation, service status, default zone set to `public`, and port `3002/tcp` listed in the public zone.

<img width="696" height="284" alt="t1" src="https://github.com/user-attachments/assets/538670e2-8b4d-476a-9366-7cc9f7b62b69" />

<img width="746" height="479" alt="t2" src="https://github.com/user-attachments/assets/4d2dbee3-256b-4271-9349-bbb481ba78b7" />

<img width="746" height="335" alt="t3" src="https://github.com/user-attachments/assets/c37e109e-cdd3-4db4-9e7c-b3fc22c4305a" />

<img width="712" height="185" alt="t4" src="https://github.com/user-attachments/assets/0bab6489-ce0c-45e9-94a6-a8aab08aa5ea" />

<img width="773" height="483" alt="t5" src="https://github.com/user-attachments/assets/5ce5fa97-b22a-4a33-8253-0e96a104d7dc" />






