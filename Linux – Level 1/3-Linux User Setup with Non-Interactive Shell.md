# Task 03: Linux User Setup with Non-Interactive Shell

## 1. Problem Statement

To accommodate the backup agent tool's specifications, the system admin team at xFusionCorp Industries requires the creation of a user with a non-interactive shell. Here's your task:



Create a user named mark with a non-interactive shell on App Server 2.

**Required configuration:**

- Username: `mark`
- Server: App Server 2 (`stapp02`)
- Shell: `/sbin/nologin`

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `useradd` – Create a Linux user
- `nologin` – Prevent interactive shell access
- `getent` and `grep` – Verify user details

## 3. Implementation Steps

### Step 1: Connect to App Server 2

From the jump host, connect using the App Server 2 login username, `steve`.

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

### Step 4: Create the User with a Non-Interactive Shell

Run:

```bash
useradd -s /sbin/nologin mark
```

The `-s` option specifies the user's login shell. Here, `/sbin/nologin` prevents the user from getting a normal interactive shell session.

### Step 5: Verify the User

Check the user's account details:

```bash
getent passwd mark
```

Check the configured shell:

```bash
grep '^mark:' /etc/passwd
```

The output should show `/sbin/nologin` as the last field.

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh steve@<APP_SERVER_2_IP>` | Connect to App Server 2 |
| `sudo su` | Switch to the root user |
| `hostname` | Verify the server |
| `useradd -s /sbin/nologin mark` | Create the user with a non-interactive shell |
| `getent passwd mark` | Display the user's account details |
| `grep '^mark:' /etc/passwd` | Check the user's shell configuration |

**Command explanation:**

- `useradd` – Creates a Linux user.
- `-s` – Specifies the login shell.
- `/sbin/nologin` – Prevents normal interactive login.
- `mark` – Name of the user being created.

## 5. Final Result

The required configuration is:

| Details | Value |
|---|---|
| Server | `stapp02` |
| Username | `mark` |
| Login Shell | `/sbin/nologin` |

The task is complete once verification confirms that the user's configured shell is `/sbin/nologin`.

## 6. What I Learned

- How to create a Linux user with a specific shell.
- What a non-interactive shell does.
- How to use the `-s` option with `useradd`.
- How to verify user details using `getent`.
- How Linux controls interactive login access.

## 7. Real-World Use Case in IT Companies

In IT companies, some Linux accounts are created for applications, services, and automated tools rather than human users.

For example, a backup agent may need a dedicated Linux account to perform its operations. Giving that account a non-interactive shell helps prevent someone from using it for a normal terminal login.

This is one way system administrators reduce unnecessary login access on Linux servers.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** User Management  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing the connection to App Server 2, user creation, and verification of the non-interactive shell.

<img width="687" height="361" alt="t1" src="https://github.com/user-attachments/assets/94efd6d5-e3cc-4415-822c-7a6aaf946d1d" />

<img width="599" height="73" alt="t2" src="https://github.com/user-attachments/assets/3d1b9919-a70b-4a71-9c5a-3565baf221b3" />

<img width="630" height="131" alt="t3" src="https://github.com/user-attachments/assets/1efb4b89-d5be-440d-97a5-10a0183a6838" />

<img width="763" height="447" alt="t4" src="https://github.com/user-attachments/assets/2a9e06eb-e657-4b9c-bacb-845511bc6a7b" />




