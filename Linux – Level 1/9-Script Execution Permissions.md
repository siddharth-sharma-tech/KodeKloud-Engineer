# Task 9: Script Execution Permissions

## 1. Problem Statement

In a bid to automate backup processes, the xFusionCorp Industries sysadmin team has developed a new bash script named xfusioncorp.sh. While the script has been distributed to all necessary servers, it lacks executable permissions on App Server 3 within the Stratos Datacenter.


Your task is to grant executable permissions to the /tmp/xfusioncorp.sh script on App Server 3. Additionally, ensure that all users have the capability to execute it (any user must be able to run it directly, for example /tmp/xfusioncorp.sh).

**Required configuration:**

- Server: App Server 3 (`stapp03`)
- Script: `/tmp/xfusioncorp.sh`
- Permissions: Read and execute for all users
- Execution: Run the script directly.

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `sudo su` – Switch to root user
- `chmod` – Change file permissions
- `ls` – Verify file permissions
- Bash – Execute the script

## 3. Implementation Steps

### Step 1: Connect to App Server 3

From the jump host, connect using the login username `banner`.

```bash
ssh banner@stapp03
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
stapp03
```

### Step 4: Navigate to the Script Directory

```bash
cd /tmp
```

### Step 5: Check Existing Permissions

```bash
ls -l xfusioncorp.sh
```

This displays the current permissions of the script.

### Step 6: Grant Read and Execute Permissions to All Users

Run:

```bash
chmod +rx xfusioncorp.sh
```

This adds read and execute permissions for the file owner, group, and others without removing existing permissions.

### Step 7: Verify Updated Permissions

```bash
ls -l xfusioncorp.sh
```

The output should contain `r` and `x` for all three permission groups.

Example:

```text
-r-xr-xr-x 1 root root 40 Nov 9 14:11 xfusioncorp.sh
```

The exact permissions may differ depending on the original permissions. The important part is that all users have read and execute permissions.

### Step 8: Execute the Script

Run:

```bash
./xfusioncorp.sh
```

The `./` tells Linux to execute the script from the current directory.

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh banner@<APP_SERVER_3_IP>` | Connect to App Server 3 |
| `sudo su` | Switch to the root user |
| `hostname` | Verify the server |
| `cd /tmp` | Navigate to the script directory |
| `ls -l xfusioncorp.sh` | Check existing permissions |
| `chmod +rx xfusioncorp.sh` | Add read and execute permissions for all users |
| `./xfusioncorp.sh` | Execute the script |

**Important command explanation:**

- `chmod` – Changes file permissions.
- `+` – Adds permissions without removing existing ones.
- `r` – Read permission.
- `x` – Execute permission.
- `a` – All users (owner, group, and others). It is implied when no user class is specified.
- `./` – Executes a file from the current directory.

## 5. Final Result

The required outcome is:

| Details | Value |
|---|---|
| Server | `stapp03` |
| Script | `/tmp/xfusioncorp.sh` |
| Read Permission | All users |
| Execute Permission | All users |
| Execution Command | `./xfusioncorp.sh` |

The task is complete once all three permission groups have read and execute permissions and the script runs successfully.

## 6. What I Learned

- How to change Linux file permissions using `chmod`.
- How to add read and execute permissions to all users.
- How to verify permissions using `ls -l`.
- How to navigate directories using `cd`.
- How to execute a script using `./`.
- How Linux permissions control access to executable scripts.

## 7. Real-World Use Case in IT Companies

In IT companies, DevOps engineers use Bash scripts to automate tasks such as backups, deployments, and server maintenance.

Sometimes different users or automated processes need to read and execute the same script.

Using `chmod +rx` allows all users to read and execute the script without changing the existing permissions unnecessarily.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** File Permissions and Script Execution  

**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing App Server 3 identification, existing script permissions, execution of `chmod +rx`, updated permissions, and script execution using `./xfusioncorp.sh`.

<img width="700" height="356" alt="t1" src="https://github.com/user-attachments/assets/5ade2284-32d2-4112-a3e9-c1307a221d4e" />

<img width="665" height="67" alt="t2" src="https://github.com/user-attachments/assets/53784108-c20b-47f2-9f5a-eddc54a5d610" />

<img width="654" height="65" alt="t3" src="https://github.com/user-attachments/assets/7e468f67-42bb-414c-86a8-7c1c055c6f62" />

<img width="747" height="353" alt="t4" src="https://github.com/user-attachments/assets/0ac08029-24c4-4d66-803a-35392c1c69cd" />

<img width="761" height="461" alt="t5" src="https://github.com/user-attachments/assets/3a83d43a-866d-4670-bad6-fccd58a53313" />




