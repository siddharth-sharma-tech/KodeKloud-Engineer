# Task 04: Service User Creation without Home Directory

## 1. Problem Statement

In response to the latest tool implementation at xFusionCorp Industries, the system admins require the creation of a service user account. Here are the specifics:



Create a user named kirsty in App Server 3 without a home directory.

**Required configuration:**

- Username: `kirsty`
- Server: App Server 3 (`stapp03`)
- Home Directory: Not required

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `useradd` – Create a Linux user
- `id` and `getent` – Verify user details
- `ls` – Check directory information

## 3. Implementation Steps

### Step 1: Connect to App Server 3

From the jump host, connect using the server login username, `banner`.

```bash
ssh banner@stapp03
```

### Step 2: Switch to Root User

```bash
sudo su
```

### Step 3: Verify the Server

Check the hostname to make sure you are connected to App Server 3.

```bash
hostname
```

Expected hostname:

```text
stapp03
```

### Step 4: Create the User Without a Home Directory

Run the following command:

```bash
useradd -M kirsty
```

The `-M` option tells Linux not to create a home directory for the user.

### Step 5: Verify the User

Check whether the user was created:

```bash
id kirsty
```

Check the user's account information:

```bash
getent passwd kirsty
```

Check the home directory field in the account information. It should not point to a newly created home directory.

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh banner@<APP_SERVER_3_IP>` | Connect to App Server 3 |
| `sudo su` | Switch to the root user |
| `hostname` | Verify the server hostname |
| `useradd -M kirsty` | Create the user without a home directory |
| `id kirsty` | Verify the user and UID |
| `getent passwd kirsty` | Display the user's account information |

**Command explanation:**

- `useradd` – Creates a Linux user.
- `-M` – Prevents creation of the user's home directory.
- `kirsty` – Name of the user being created.

## 5. Final Result

The required configuration is:

| Details | Value |
|---|---|
| Server | `stapp03` |
| Username | `kirsty` |
| Home Directory | Not created |

The task is complete once the user exists and verification confirms that no home directory was created.

## 6. What I Learned

- How to create a Linux user without a home directory.
- How to use the `-M` option with `useradd`.
- How to verify user information using `id` and `getent`.
- How service accounts can be created with specific requirements.

## 7. Real-World Use Case in IT Companies

In IT companies, some users are created only to run applications, services, or automated tools.

These accounts may not need a personal home directory because they are not used for normal human login.

Creating users without home directories helps avoid unnecessary directories and keeps server accounts organized.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** User Management  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing the connection to App Server 3, user creation, and verification that the user exists without a home directory.

<img width="689" height="357" alt="t1" src="https://github.com/user-attachments/assets/bf8a08bf-8aa8-4cfa-83e2-39b74b0b052e" />

<img width="650" height="68" alt="t2" src="https://github.com/user-attachments/assets/a1911c54-a5b1-41fd-b9c8-18f368cad468" />

<img width="648" height="125" alt="t3" src="https://github.com/user-attachments/assets/bf721163-651c-4cd8-9716-559607f6cee6" />

<img width="743" height="451" alt="t4" src="https://github.com/user-attachments/assets/ca6722ab-5a0e-4904-b251-600fed933a4e" />






