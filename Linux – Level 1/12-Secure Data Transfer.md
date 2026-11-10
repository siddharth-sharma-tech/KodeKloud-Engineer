# Task 12: Secure Data Transfer

## 1. Problem Statement

A Nautilus developer has stored confidential data on the jump host within Stratos DC. To ensure security and compliance, this data must be transferred to one of the app servers. Given developers lack direct access to these servers, the system admin team has been enlisted for assistance.



Copy /tmp/nautilus.txt.gpg file from jump server to App Server 2 placing it in the directory /home/app.

**Required configuration:**

- Source Server: Jump Host (`jump-host`)
- Destination Server: App Server 2 (`stapp02`)
- Source File: `/tmp/nautilus.txt.gpg`
- Destination Directory: `/home/app`
- Destination File: `/home/app/nautilus.txt.gpg`
- Operation: Copy the encrypted file

## 2. Tools & Technologies Used

- Linux
- SSH – Secure server connection
- SCP – Secure file transfer
- `sudo su` – Switch to root user when required
- `ls` – Verify file existence

## 3. Implementation Steps

### Step 1: Connect to the Jump Host Server

Connect using the login username `thor`.

```bash
ssh thor@jump-host
```

### Step 2: Verify the Server

```bash
hostname
```

Confirm that you are connected to the Jump Host Server.

### Step 3: Check the Source File

Verify that the encrypted file exists:

```bash
ls -l /tmp/nautilus.txt.gpg
```

### Step 4: Copy the File to App Server 2

Run the following command from the Jump Host:

```bash
scp /tmp/nautilus.txt.gpg steve@stapp02:/home/app/
```

This transfers the file securely to the `/home/app` directory on App Server 2.

If prompted, authenticate using the configured SSH credentials.

### Step 5: Connect to App Server 2

```bash
ssh steve@stapp02
```

### Step 6: Switch to Root User if Required

```bash
sudo su
```

### Step 7: Verify the Transferred File

Check the destination file:

```bash
ls -l /home/app/nautilus.txt.gpg
```

The file should be present in `/home/app`.

You can also verify the file type:

```bash
file /home/app/nautilus.txt.gpg
```

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh thor@jump-host` | Connect to the Jump Host |
| `hostname` | Verify the server |
| `ls -l /tmp/nautilus.txt.gpg` | Check the source file |
| `scp /tmp/nautilus.txt.gpg steve@stapp02:/home/app/` | Transfer the file to App Server 2 |
| `ssh steve@stapp02` | Connect to App Server 2 |
| `sudo su` | Switch to the root user |
| `ls -l /home/app/nautilus.txt.gpg` | Verify the transferred file |
| `file /home/app/nautilus.txt.gpg` | Identify the file type |

**Important command explanation:**

- `scp` – Securely copies files between servers.
- `/tmp/nautilus.txt.gpg` – Source file on the Jump Host.
- `steve` – Login username on App Server 2.
- `stapp02` – IP address of App Server 2.
- `:` – Separates the remote server address from its destination path.
- `/home/app/` – Destination directory.

## 5. Final Result

The required outcome is:

| Details | Value |
|---|---|
| Source Server | Jump Host |
| Destination Server | `stapp02` |
| Source File | `/tmp/nautilus.txt.gpg` |
| Destination | `/home/app/nautilus.txt.gpg` |
| Transfer Method | SCP |
| Operation | Copy |

The task is complete once the file is present in `/home/app` on App Server 2.

The original file remains on the Jump Host because SCP copies the file rather than moving it.

## 6. What I Learned

- How to transfer files between Linux servers using SCP.
- How SCP uses SSH for secure file transfer.
- How to specify a remote server and destination directory.
- How to verify transferred files.
- How to work with encrypted `.gpg` files.
- How system administrators transfer files between servers.

## 7. Real-World Use Case in IT Companies

In IT companies, developers and administrators often need to transfer application files, configuration files, and backup files between servers.

For example, a system administrator may need to transfer an encrypted backup from a jump server to an application server.

SCP helps transfer files securely over SSH without exposing the file contents during network transmission.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** Secure File Transfer using SCP  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing Jump Host identification, source file verification, SCP transfer command, connection to App Server 2, and successful destination file verification.

<img width="685" height="87" alt="t1" src="https://github.com/user-attachments/assets/2023a7e4-77db-430b-96a8-b94450d48b15" />

<img width="684" height="67" alt="t2" src="https://github.com/user-attachments/assets/fc560774-d8be-4d08-993c-0cc8d763a9f6" />

<img width="711" height="87" alt="t3" src="https://github.com/user-attachments/assets/7d2cddf3-a65f-4cbc-a090-8207d89776c2" />

<img width="671" height="103" alt="t4" src="https://github.com/user-attachments/assets/106ce2d0-3040-4e40-b39e-d77c5310e265" />

<img width="753" height="458" alt="t5" src="https://github.com/user-attachments/assets/d923c9fc-9025-4c52-a576-0b7a358fefbe" />






