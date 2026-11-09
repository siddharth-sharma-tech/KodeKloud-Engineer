# Task 06: Linux User Data Transfer

## 1. Problem Statement

Due to an accidental data mix-up, user data was unintentionally mingled on Nautilus App Server 2 at the /home/usersdata location by the Nautilus production support team in Stratos DC. To rectify this, specific user data needs to be filtered and relocated. Here are the details:



Locate all files (excluding directories) owned by user kirsty within the /home/usersdata directory on App Server 2. Copy these files while preserving the directory structure to the /ecommerce directory.

**Required configuration:**

- Server: App Server 2 (`stapp02`)
- Source Directory: `/home/usersdata`
- File Owner: `kirsty`
- Destination Directory: `/ecommerce`
- Operation: Copy files, not move them

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `find` – Locate files based on ownership and type
- `cp` – Copy files
- `mkdir` – Create the destination directory
- `ls` – Verify copied files

## 3. Implementation Steps

### Step 1: Connect to App Server 2

From the jump host, connect using the server login username `steve`.

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

### Step 4: Check the Source Directory

List the contents of the source directory:

```bash
ls -l /home/usersdata
```

### Step 5: Find Files Owned by Kirsty

Run:

```bash
find /home/usersdata -type f -user kirsty
```

This displays only regular files owned by `kirsty`. Directories are excluded.

### Step 6: Create the Destination Directory

```bash
mkdir -p /ecommerce
```

The `-p` option creates the directory if it does not already exist.

### Step 7: Copy Files While Preserving Directory Structure

Run the following command:

```bash
find /home/usersdata -type f -user kirsty -exec cp --parents {} /ecommerce \;
```

This command:

- Searches inside `/home/usersdata`.
- Finds only regular files owned by `kirsty`.
- Excludes directories.
- Copies each matching file to `/ecommerce`.
- Preserves the original directory structure using `--parents`.
- Executes the copy command separately for each matching file using `\;`.

**Example:**

If the original file is:

```text
/home/usersdata/project1/config/settings.conf
```

The copied file will be located at:

```text
/ecommerce/home/usersdata/project1/config/settings.conf
```

Notice that the full original path is preserved, including `/home/usersdata`.

### Step 8: Verify the Copied Files

Check the destination directory:

```bash
ls -lR /ecommerce
```

You can also list all copied files:

```bash
find /ecommerce -type f
```

Compare the destination contents with the original matching files under `/home/usersdata` to confirm that the files were copied correctly.

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh steve@<APP_SERVER_2_IP>` | Connect to App Server 2 |
| `sudo su` | Switch to the root user |
| `hostname` | Verify the server |
| `ls -l /home/usersdata` | List source directory contents |
| `find /home/usersdata -type f -user kirsty` | Find regular files owned by Kirsty |
| `mkdir -p /ecommerce` | Create the destination directory |
| `find /home/usersdata -type f -user kirsty -exec cp --parents {} /ecommerce \;` | Copy matching files while preserving directory structure |
| `ls -lR /ecommerce` | Verify copied files and directories |

**Important command explanation:**

- `find` – Searches for files and directories.
- `-type f` – Selects regular files only, excluding directories.
- `-user kirsty` – Selects files owned by user `kirsty`.
- `-exec` – Executes a command on each matching file.
- `cp` – Copies files.
- `--parents` – Preserves the original directory path.
- `{}` – Represents the file found by `find`.
- `/ecommerce` – Destination directory.
- `\;` – Marks the end of the command executed by `-exec` for each matching file.

## 5. Final Result

The required outcome is:

| Details | Value |
|---|---|
| Server | `stapp02` |
| File Owner | `kirsty` |
| Source | `/home/usersdata` |
| Destination | `/ecommerce` |
| File Selection | Regular files only |
| Directory Structure | Preserved |
| Operation | Copy |

The task is complete once all matching files have been copied to `/ecommerce` and their directory structure has been verified.

The original files remain in `/home/usersdata` because this task requires copying, not moving them.

## 6. What I Learned

- How to find files owned by a specific Linux user.
- How to exclude directories using `-type f`.
- How to use `find` with the `-user` option.
- How to combine `find` and `cp` using `-exec`.
- How to preserve directory structure using `cp --parents`.
- How `\;` executes the copy command for each matching file.
- How to verify copied files.

## 7. Real-World Use Case in IT Companies

In IT companies, different users may store application files, configuration files, and project data on the same Linux server.

If administrators need to collect files belonging to a particular user, they can use `find` to identify those files based on ownership.

They can then copy the files to another location while keeping the original directory structure.

For example, this is useful when organizing application data or preparing user-specific files for migration without changing the original files.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** File Management and Ownership  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing server identification, locating files owned by `kirsty`, copying files to `/ecommerce`, and verifying the copied directory structure.

<img width="689" height="359" alt="t1" src="https://github.com/user-attachments/assets/596d91f2-8ade-480a-b1e3-979b1ed4ce2d" />

<img width="675" height="68" alt="t2" src="https://github.com/user-attachments/assets/58b2fb4c-8218-4c45-9dce-61998c74e72e" />

<img width="677" height="433" alt="t3" src="https://github.com/user-attachments/assets/f737b876-2a7f-478b-a9dc-b1d5d0f19be7" />

<img width="745" height="47" alt="t4" src="https://github.com/user-attachments/assets/a7bb7284-731f-4b9c-938d-c2a9c6d0f783" />

<img width="745" height="466" alt="t5" src="https://github.com/user-attachments/assets/622ef9c0-06eb-4f4f-9461-9c6153fd7c0c" />

<img width="783" height="475" alt="t6" src="https://github.com/user-attachments/assets/9453fba3-b225-4bea-bdd7-8c30c39e8aa9" />



