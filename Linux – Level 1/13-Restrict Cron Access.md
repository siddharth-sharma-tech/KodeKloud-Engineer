# Task 13: Restrict Cron Access

## 1. Problem Statement

In alignment with security compliance standards, the Nautilus project team has opted to impose restrictions on crontab access. Specifically, only designated users will be permitted to create or update cron jobs.



Configure crontab access on App Server 2 as follows: Allow crontab access to yousuf user while denying access to the jerome user.

**Required configuration:**

- Server: App Server 2 (`stapp02`)
- Allowed User: `yousuf`
- Denied User: `jerome`
- Configuration Files: `/etc/cron.allow` and `/etc/cron.deny`

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `sudo su` – Switch to root user
- `vi` – Edit configuration files
- `crontab` – Manage scheduled jobs
- `cat` – Verify configuration files

## 3. Implementation Steps

### Step 1: Connect to App Server 2

From the jump host, connect using the login username `steve`.

```bash
ssh steve@stapp02
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
stapp02
```

### Step 4: Allow Crontab Access to Yousef

Create or edit the `/etc/cron.allow` file:

```bash
vi /etc/cron.allow
```

Add the following username:

```text
yousuf
```

Save and exit using `Esc`, then `:wq`.

This allows `yousuf` to use crontab.

### Step 5: Deny Crontab Access to Jerome

Create or edit the `/etc/cron.deny` file:

```bash
vi /etc/cron.deny
```

Add:

```text
jerome
```

Save and exit using `Esc`, then `:wq`.

This records `jerome` as a user who should not have crontab access.

### Step 6: Verify the Configuration

Check the allow file:

```bash
cat /etc/cron.allow
```

Expected entry:

```text
yousuf
```

Check the deny file:

```bash
cat /etc/cron.deny
```

Expected entry:

```text
jerome
```

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh steve@<APP_SERVER_2_IP>` | Connect to App Server 2 |
| `sudo su` | Switch to root user |
| `hostname` | Verify the server |
| `vi /etc/cron.allow` | Allow selected users to use crontab |
| `vi /etc/cron.deny` | Deny selected users from using crontab |
| `cat /etc/cron.allow` | Verify allowed users |
| `cat /etc/cron.deny` | Verify denied users |

**Important command explanation:**

- `/etc/cron.allow` – Contains usernames permitted to use crontab.
- `/etc/cron.deny` – Contains usernames denied access to crontab when the allow file is not controlling access.
- `vi` – Opens a file for editing.
- `cat` – Displays file contents.

**Important:** On standard Linux cron implementations, if `/etc/cron.allow` exists, only users listed in that file are allowed to use crontab. `/etc/cron.deny` is generally checked only when `/etc/cron.allow` does not exist. Therefore, listing only `yousuf` in `cron.allow` also prevents `jerome` from using crontab.

## 5. Final Result

The required configuration is:

| User | Crontab Access |
|---|---|
| `yousuf` | Allowed |
| `jerome` | Denied |

The task is complete once the configuration files contain the required usernames and access behavior is verified.

## 6. What I Learned

- How Linux controls access to crontab.
- How to use `/etc/cron.allow`.
- How to use `/etc/cron.deny`.
- How to edit configuration files using `vi`.
- How to verify configuration using `cat`.
- How to restrict scheduled job management to selected users.

## 7. Real-World Use Case in IT Companies

In IT companies, cron jobs are used to automate backups, cleanup tasks, monitoring scripts, and other scheduled operations.

Not every employee should be able to create or modify scheduled jobs on production servers.

System administrators can restrict crontab access to approved users so that only authorized team members can manage scheduled tasks.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** Cron Management and User Access Control  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing App Server 2 identification, editing of `/etc/cron.allow` and `/etc/cron.deny`, and verification of the configured usernames.

<img width="704" height="431" alt="t1" src="https://github.com/user-attachments/assets/f7fadd45-55b0-484b-8c64-13b4aa422fb0" />

<img width="685" height="70" alt="t2" src="https://github.com/user-attachments/assets/3807f60b-92e8-40ba-a9b5-431c01c0ec61" />

<img width="645" height="29" alt="t3" src="https://github.com/user-attachments/assets/0e453c74-736c-4106-8acf-7be69f3950f7" />

<img width="725" height="471" alt="t4" src="https://github.com/user-attachments/assets/98f84dfb-711c-40d0-9cae-0996452fd16f" />

<img width="631" height="30" alt="t5" src="https://github.com/user-attachments/assets/e87e6f40-1e45-4805-8c6e-06e2890fd54a" />

<img width="703" height="477" alt="t6" src="https://github.com/user-attachments/assets/bcc2460c-6979-4e51-8159-a457d83a68e9" />

<img width="651" height="107" alt="t10" src="https://github.com/user-attachments/assets/0f0af607-2f08-4c07-8ae6-9217b0bdcd45" />

<img width="760" height="479" alt="t11" src="https://github.com/user-attachments/assets/66480718-684b-4872-b62d-70e55b235896" />







