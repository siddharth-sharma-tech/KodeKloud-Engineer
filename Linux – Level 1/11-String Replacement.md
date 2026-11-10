# Task 11: String Replacement

## 1. Problem Statement

At xFusionCorp Industries, the Stratos Datacenter houses a jump host server that stores template XML files essential for the Nautilus application. Prior to their use, these files need to be populated with valid data. As part of regular maintenance, the system administration team utilizes various string and file manipulation commands to prepare these templates.



Your task is to substitute all occurrences of the string Sample with Echo-Location within the XML file located at /root/nautilus.xml on the jump host server.

**Required configuration:**

- Server: Jump Host Server (`jump-host`)
- File: `/root/nautilus.xml`
- Existing String: `Sample`
- Replacement String: `Echo-Location`
- Operation: Replace all occurrences

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `sudo su` – Switch to root user
- `sed` – Search and replace text
- `grep` – Verify the replacement
- `cat` – Display file contents

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

### Step 4: Check the XML File

Display the file contents:

```bash
cat /root/nautilus.xml
```

### Step 5: Replace All Occurrences of Sample

Run:

```bash
sed -i 's/Sample/Echo-Location/g' /root/nautilus.xml
```

This replaces every occurrence of `Sample` with `Echo-Location` directly inside the XML file.

### Step 6: Verify the Replacement

Check whether the old string still exists:

```bash
grep -n 'Sample' /root/nautilus.xml
```

If there is no output, no matching occurrences remain.

Check the replacement string:

```bash
grep -n 'Echo-Location' /root/nautilus.xml
```

You can also display the updated file:

```bash
cat /root/nautilus.xml
```

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh thor@<JUMP_HOST_IP>` | Connect to the Jump Host Server |
| `sudo su` | Switch to the root user |
| `hostname` | Verify the server |
| `cat /root/nautilus.xml` | Display the XML file |
| `sed -i 's/Sample/Echo-Location/g' /root/nautilus.xml` | Replace all occurrences in the file |
| `grep -n 'Sample' /root/nautilus.xml` | Check for remaining old strings |
| `grep -n 'Echo-Location' /root/nautilus.xml` | Verify the replacement |
 
**Important command explanation:**

- `sed` – Used to search and modify text.
- `-i` – Updates the original file directly.
- `s` – Stands for substitute.
- `Sample` – Original string to find.
- `Echo-Location` – Replacement string.
- `g` – Replaces all occurrences on each line, not just the first one.
- `grep -n` – Searches for a string and displays matching line numbers.

## 5. Final Result

The required outcome is:

| Details | Value |
|---|---|
| Server | Jump Host (`jump-host`) |
| File | `/root/nautilus.xml` |
| Original String | `Sample` |
| Replacement String | `Echo-Location` |
| Operation | Replace all occurrences |

The task is complete once the XML file contains the replacement string and no occurrences of the old string remain.

## 6. What I Learned

- How to search for text inside a Linux file.
- How to use `sed` for search and replace operations.
- How to replace multiple occurrences using the `g` option.
- How to modify a file directly using `sed -i`.
- How to verify file changes using `grep`.
- How Linux commands help automate configuration file updates.

## 7. Real-World Use Case in IT Companies

In IT companies, system administrators and DevOps engineers regularly work with configuration files, XML templates, and application settings.

For example, an application template may contain placeholder values that need to be replaced before deployment.

Instead of manually editing every occurrence, engineers can use `sed` to replace values quickly and consistently.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** File Management and Text Processing  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing Jump Host identification, original XML file contents, execution of the `sed` replacement command, and verification that `Sample` was replaced with `Echo-Location`.

<img width="665" height="90" alt="t1" src="https://github.com/user-attachments/assets/2ae4eb1e-1a28-495b-9658-437a28b059d3" />

<img width="729" height="478" alt="t2" src="https://github.com/user-attachments/assets/8e3b6a4c-9ad5-4c69-9493-2c46e576887c" />

<img width="687" height="67" alt="t3" src="https://github.com/user-attachments/assets/ad61076e-a799-4735-ab7b-ad999ecbaeb0" />

<img width="741" height="475" alt="t4" src="https://github.com/user-attachments/assets/97b2e3d3-6610-4bbb-8a2f-21b5d8f5db7f" />

<img width="754" height="473" alt="t5" src="https://github.com/user-attachments/assets/81707745-7fe6-44fd-9018-ec7c6b1dc87f" />




