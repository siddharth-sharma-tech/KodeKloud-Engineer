# Task 14: Default GUI Boot Configuration

## 1. Problem Statement

With the installation of new tools on the app servers within the Stratos Datacenter, certain functionalities now necessitate graphical user interface (GUI) access.



Adjust the default runlevel on all App servers in Stratos Datacenter to enable GUI booting by default. It's imperative not to initiate a server reboot after completing this task.

**Required configuration:**

- App Server 1: `stapp01`
- App Server 2: `stapp02`
- App Server 3: `stapp03`
- Default Target: `graphical.target`
- Reboot: Not allowed

## 2. Tools & Technologies Used

- Linux
- SSH
- `sudo su` – Switch to root user
- `systemctl` – Manage systemd targets
- `rpm` – Check installed packages
- `polkit` – Policy authorization service used by system components

## 3. Implementation Steps

I performed the same configuration on all three App Servers.

### Step 1: Connect to App Server 1

Connect using the login username `tony`.

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

### Step 4: Check the Polkit Package

Run:

```bash
rpm -q polkit
```

This checks whether the Polkit package is installed.

If installed, the command displays its package version. If it is missing, it reports that the package is not installed.

### Step 5: Check the Current Default Target

```bash
systemctl get-default
```

This displays the current default systemd target.

### Step 6: Set GUI as the Default Target

Run:

```bash
systemctl set-default graphical.target
```

This configures the system to boot into graphical mode on its next startup.

### Step 7: Verify the New Default Target

```bash
systemctl get-default
```

Expected output:

```text
graphical.target
```

### Step 8: Repeat on App Server 2

Connect using `steve`.

```bash
ssh steve@stapp02
sudo su
```

Verify the hostname:

```bash
hostname
```

Expected hostname: `stapp02`

Check Polkit:

```bash
rpm -q polkit
```

Set the default target:

```bash
systemctl set-default graphical.target
```

Verify:

```bash
systemctl get-default
```

### Step 9: Repeat on App Server 3

Connect using `banner`.

```bash
ssh banner@stapp03
sudo su
```

Verify the hostname:

```bash
hostname
```

Expected hostname: `stapp03`

Check Polkit:

```bash
rpm -q polkit
```

Set the default target:

```bash
systemctl set-default graphical.target
```

Verify:

```bash
systemctl get-default
```

**No reboot command should be executed on any server.**

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh` | Connect to an App Server |
| `sudo su` | Switch to root user |
| `hostname` | Verify the server |
| `rpm -q polkit` | Check whether Polkit is installed |
| `systemctl get-default` | Check the current default target |
| `systemctl set-default graphical.target` | Set GUI as the default boot target |

**Important command explanation:**

- `rpm -q polkit` – Checks the installed Polkit package.
- `systemctl` – Manages systemd services and targets.
- `get-default` – Displays the default systemd target.
- `set-default` – Changes the default systemd target.
- `graphical.target` – Target used for graphical login and multi-user GUI environments.

**What is Polkit?**

Polkit (PolicyKit) is an authorization service in Linux. It helps control whether regular users are allowed to perform privileged operations through system services and graphical applications.

It is related to GUI environments, but it does not configure the default runlevel. The actual command for this task is `systemctl set-default graphical.target`.

## 5. Final Result

The required configuration is:

| Server | Default Target | Reboot |
|---|---|---|
| `stapp01` | `graphical.target` | Not performed |
| `stapp02` | `graphical.target` | Not performed |
| `stapp03` | `graphical.target` | Not performed |

The task is complete once `systemctl get-default` displays `graphical.target` on all three servers.

The running servers remain in their current state because no reboot or target switch is performed.

## 6. What I Learned

- What systemd targets are.
- The difference between `multi-user.target` and `graphical.target`.
- How to change the default boot target using `systemctl`.
- How to check installed packages using `rpm`.
- What Polkit does in Linux.
- How to configure multiple servers without rebooting them.

## 7. Real-World Use Case in IT Companies

In IT companies, some application servers require a graphical environment to run administration tools or GUI-based applications.

System administrators can configure these servers to start in graphical mode by default.

Using `systemctl set-default graphical.target` changes the boot configuration without immediately interrupting running applications or services.

This is useful when administrators need to prepare servers for GUI access while avoiding an unnecessary restart during working hours.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** Systemd Targets and Runlevel Management  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing server identification, Polkit package checks, default target configuration, and verification of `graphical.target` on all three App Servers.

<img width="721" height="399" alt="t1" src="https://github.com/user-attachments/assets/b06c1854-e6bf-4ab2-873c-280b8eb34cfc" />

<img width="746" height="225" alt="t2" src="https://github.com/user-attachments/assets/a7ebdbe8-ecac-4606-8b35-07db0afe89d1" />

<img width="707" height="398" alt="t3" src="https://github.com/user-attachments/assets/13dd55a0-4777-4460-96ce-40f365e46141" />

<img width="744" height="227" alt="t4" src="https://github.com/user-attachments/assets/176da553-ef11-49b9-b174-e6cea64b659f" />

<img width="695" height="396" alt="t5" src="https://github.com/user-attachments/assets/c9fc58ae-cee6-425c-adb9-9bbea565d073" />

<img width="744" height="229" alt="t6" src="https://github.com/user-attachments/assets/c7117d46-88ca-4c1f-a30f-4e34230a2bdb" />

<img width="767" height="490" alt="t7" src="https://github.com/user-attachments/assets/13b57ba8-3386-49a1-87f3-3003fd08b5c5" />








