# Task 8: Data Backup for Developer

## 1. Problem Statement

The jump host server hosts a directory named /data, serving as a repository for various developers non-confidential data. Developer ammar has requested a copy of their data stored in /data/ammar. The System Admin team has provided the following steps to fulfill this request:



a. Create a compressed archive named ammar.tar.gz of the /data/ammar directory.

b. Transfer the archive to the /home directory on the Jump Host Server.

**Required configuration:**

- Server: Jump Host Server (`jump-host`)
- Source Directory: `/data/ammar`
- Archive Name: `ammar.tar.gz`
- Destination Directory: `/home`
- Operation: Create, compress, and move the archive

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `sudo su` – Switch to root user
- `tar` – Create and compress an archive
- `mv` – Move the archive
- `ls` – Verify the archive

## 3. Implementation Steps

### Step 1: Connect to the Jump Host Server

Connect using the login username `thor`.

```bash
ssh thor@jump-host
```

### Step 2: Switch to Root User

```bash
sudo su
```

### Step 3: Verify the Server

```bash
hostname
```

Confirm that you are connected to the Jump Host Server.

### Step 4: Check the Source Directory

List the contents of `/data/ammar`.

```bash
ls -l /data/ammar
```

This helps confirm that the directory exists and contains the developer's data.

### Step 5: Create the Compressed Archive

Run:

```bash
tar -czvf ammar.tar.gz /data/ammar
```

This creates a compressed archive named `ammar.tar.gz` in the current working directory.

### Step 6: Move the Archive to `/home`

Run:

```bash
mv ammar.tar.gz /home/
```

This moves the archive from the current working directory to `/home`.

### Step 7: Verify the Archive

Check whether the archive exists in `/home`.

```bash
ls -lh /home/ammar.tar.gz
```

To view the contents without extracting the archive:

```bash
tar -tzvf /home/ammar.tar.gz
```

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh thor@<JUMP_HOST_IP>` | Connect to the Jump Host Server |
| `sudo su` | Switch to the root user |
| `hostname` | Verify the server |
| `ls -l /data/ammar` | Check the source directory |
| `tar -czvf ammar.tar.gz /data/ammar` | Create a compressed archive |
| `mv ammar.tar.gz /home/` | Move the archive to `/home` |
| `ls -lh /home/ammar.tar.gz` | Verify the archive |
| `tar -tzvf /home/ammar.tar.gz` | List the archive contents |

**Important command explanation:**

- `tar` – Used to create and manage archives.
- `-c` – Creates a new archive.
- `-z` – Compresses the archive using gzip.
- `-v` – Displays the files being archived.
- `-f` – Specifies the archive filename.
- `ammar.tar.gz` – Name of the compressed archive.
- `/data/ammar` – Source directory.
- `mv` – Moves a file from one location to another.
- `/home/` – Destination directory.

## 5. Final Result

The required outcome is:

| Details | Value |
|---|---|
| Server | Jump Host (`jump-host`) |
| Source Directory | `/data/ammar` |
| Archive Name | `ammar.tar.gz` |
| Destination | `/home/ammar.tar.gz` |
| Compression | gzip |

The task is complete once the archive is available at `/home/ammar.tar.gz` and its contents can be listed successfully.

The original `/data/ammar` directory remains unchanged because we created a copy in archive form and moved only the archive.

## 6. What I Learned

- How to create compressed archives using `tar`.
- How to use `-czvf` options.
- How to move files using the `mv` command.
- How to store archives in a specific directory.
- How to verify archive files using `ls`.
- How to inspect archive contents without extracting them.

## 7. Real-World Use Case in IT Companies

In IT companies, developers sometimes need copies of their project data for backup or sharing.

System administrators can use `tar` to combine a directory and its files into one compressed archive.

They can then use `mv` to place the archive in a designated storage location.

This makes project data easier to organize, store, and transfer while keeping the original files unchanged.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** File Management and Archiving  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing Jump Host identification, source directory contents, archive creation, moving the archive to `/home`, and final verification.

<img width="704" height="88" alt="t1" src="https://github.com/user-attachments/assets/6fb85acd-5cf9-4174-8540-b1fb475b8706" />

<img width="645" height="123" alt="t2" src="https://github.com/user-attachments/assets/8c652883-00c4-47b5-a54d-e3286cfefa48" />

<img width="646" height="204" alt="t3" src="https://github.com/user-attachments/assets/9791fd92-12aa-4ecc-8e7b-db0d9aa86ec1" />

<img width="678" height="183" alt="t4" src="https://github.com/user-attachments/assets/cdef9d58-1f8b-4bf8-96ab-ded4572ab764" />

<img width="763" height="480" alt="t5" src="https://github.com/user-attachments/assets/912bfe38-f942-48f6-99d3-80207147cff8" />




