# Task 7: Secure Root SSH Access

## 1. Problem Statement

Following security audits, the xFusionCorp Industries security team has rolled out new protocols, including the restriction of direct root SSH login.



Your task is to disable direct SSH root login on all app servers (stapp01, stapp02 and stapp03) within the Stratos Datacenter. Make sure the change is applied to the running SSH service on each server.

**Required configuration:**

- App Server 1: `stapp01`
- App Server 2: `stapp02`
- App Server 3: `stapp03`
- Configuration File: `/etc/ssh/sshd_config`
- Required Setting: `PermitRootLogin no`

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `vi` – Edit the SSH configuration file
- `sshd` – OpenSSH server configuration
- `systemctl` – Manage the SSH service
- `grep` – Verify configuration settings

## 3. Implementation Steps

I performed the same configuration on all three App Servers.

### Step 1: Connect to App Server 1

From the jump host, connect using the server login username `tony`.

```bash
ssh tony@stapp01
```

### Step 2: Switch to Root User

```bash
sudo su
```

### Step 3: Verify the Server

```bash
hostname
```

Expected hostname:

```text
stapp01
```

### Step 4: Open the SSH Configuration File

Open the SSH configuration file using `vi`.

```bash
vi /etc/ssh/sshd_config
```

Inside the file:

1. Press `/` and search for `PermitRootLogin`.
2. Press `Enter`.
3. Find the existing `PermitRootLogin` setting.
4. Press `i` to enter insert mode.
5. Change the setting to:

```text
PermitRootLogin no
```

6. Press `Esc`.
7. Type `:wq` and press `Enter` to save and exit.

If the setting does not exist, add `PermitRootLogin no` in the global configuration section, outside any `Match` block.

### Step 5: Verify the Configuration

Run:

```bash
grep -i '^PermitRootLogin' /etc/ssh/sshd_config
```

Expected output:

```text
PermitRootLogin no
```

### Step 6: Check SSH Configuration Syntax

Before applying the change, check the SSH configuration for errors.

```bash
sshd -t
```

If there is no output, the configuration syntax check has passed.

### Step 7: Restart the SSH Service

Apply the updated configuration:

```bash
systemctl restart sshd
```

Check the SSH service status:

```bash
systemctl status sshd
```

Make sure the service is active and running.

### Step 8: Repeat on App Server 2

Connect to App Server 2 using `steve`.

```bash
ssh steve@stapp02
```

Switch to root:

```bash
sudo su
```

Verify the hostname:

```bash
hostname
```

Expected hostname: `stapp02`

Repeat Steps 4–7 to update the SSH configuration, validate it, and restart the SSH service.

### Step 9: Repeat on App Server 3

Connect to App Server 3 using `banner`.

```bash
ssh banner@stapp03
```

Switch to root:

```bash
sudo su
```

Verify the hostname:

```bash
hostname
```

Expected hostname: `stapp03`

Repeat Steps 4–7 to update the SSH configuration, validate it, and restart the SSH service.

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh` | Connect to an App Server |
| `sudo su` | Switch to the root user |
| `hostname` | Verify the server |
| `vi /etc/ssh/sshd_config` | Open the SSH configuration file |
| `PermitRootLogin no` | Disable direct root SSH login |
| `grep -i '^PermitRootLogin' /etc/ssh/sshd_config` | Check the configured setting |
| `sshd -t` | Check SSH configuration syntax |
| `systemctl restart sshd` | Restart the SSH service |
| `systemctl status sshd` | Check SSH service status |

**Important command explanation:**

- `vi` – Opens a text editor in the terminal.
- `sshd_config` – Main configuration file for the OpenSSH server.
- `PermitRootLogin no` – Prevents root from logging in directly through SSH.
- `sshd -t` – Checks the SSH configuration for syntax errors.
- `systemctl restart sshd` – Restarts the SSH service and applies the updated configuration.
- `systemctl status sshd` – Displays the current SSH service status.

## 5. Final Result

The required configuration on all three App Servers is:

| Server | SSH Setting | Expected Value |
|---|---|---|
| `stapp01` | `PermitRootLogin` | `no` |
| `stapp02` | `PermitRootLogin` | `no` |
| `stapp03` | `PermitRootLogin` | `no` |

The task is complete once:

- Direct root SSH login is disabled on all three servers.
- SSH configuration syntax checks pass.
- The SSH service is active and running after the changes.

## 6. What I Learned

- How to edit SSH configuration files using `vi`.
- How to disable direct root SSH login.
- What `PermitRootLogin no` does.
- How to validate SSH configuration using `sshd -t`.
- How to restart and check the SSH service using `systemctl`.
- How to apply security configuration changes across multiple Linux servers.

## 7. Real-World Use Case in IT Companies

In IT companies, administrators manage Linux servers that host applications and business services.

Allowing direct root SSH login can increase security risks because the root account has full administrative privileges.

Instead, administrators connect using their individual accounts and use `sudo` when they need administrative access.

Disabling direct root SSH login helps protect servers and makes it easier to track which administrator performed an action.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** SSH Configuration and Security  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing server identification, SSH configuration changes, configuration validation, and successful SSH service status on all three App Servers.

<img width="704" height="301" alt="t1" src="https://github.com/user-attachments/assets/628af8f4-2c31-489e-bbd6-7833ec8252d8" />

<img width="697" height="71" alt="t2" src="https://github.com/user-attachments/assets/930624da-7082-4d2b-a854-804ef5985b64" />

<img width="687" height="26" alt="t3" src="https://github.com/user-attachments/assets/688226fa-2ac7-4851-8de0-a88335bf0aaf" />

<img width="733" height="149" alt="t4" src="https://github.com/user-attachments/assets/9813130d-15ad-4c7e-a843-f46ff9a09607" />

<img width="781" height="393" alt="t5" src="https://github.com/user-attachments/assets/57d6194a-7e4d-47e2-a072-188649026649" />

<img width="781" height="354" alt="t6" src="https://github.com/user-attachments/assets/349d23f0-2777-4f5e-8cc4-8c1be20ab25b" />

<img width="791" height="68" alt="t7" src="https://github.com/user-attachments/assets/a9916614-2c45-461a-bfe0-1dcb3de08c33" />

<img width="780" height="52" alt="t8" src="https://github.com/user-attachments/assets/06ed4319-8ec1-4864-aaa1-1277a4676fee" />

<img width="810" height="157" alt="t9" src="https://github.com/user-attachments/assets/c5bdd674-404b-47dd-ac6e-79c6131020bd" />

<img width="763" height="391" alt="t10" src="https://github.com/user-attachments/assets/eaf2b96b-8180-467e-9edd-a3fad37dbe46" />

<img width="751" height="353" alt="t11" src="https://github.com/user-attachments/assets/c9d3c568-c437-4e73-b17a-67cfb461d1a5" />

<img width="765" height="67" alt="t12" src="https://github.com/user-attachments/assets/0c6df73d-4fcd-487c-8e05-b705f1d8702a" />

<img width="775" height="31" alt="t13" src="https://github.com/user-attachments/assets/c81fb822-28c6-42eb-a188-6ed9e2830e01" />

<img width="761" height="146" alt="t14" src="https://github.com/user-attachments/assets/17023e72-c052-4746-a006-77f27ff275f2" />

<img width="791" height="397" alt="t15" src="https://github.com/user-attachments/assets/ebabb770-e066-48bc-b17c-0006cfb997c3" />

<img width="773" height="468" alt="t16" src="https://github.com/user-attachments/assets/8abb573e-e28d-4550-b736-1fc1d9208a3e" />














