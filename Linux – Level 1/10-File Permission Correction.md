# Task 16: File Permission Correction

## 1. After conducting a security audit within the Stratos DC, the Nautilus security team discovered misconfigured permissions on critical files. To address this, corrective actions are being taken by the production support team. Specifically, the file named /etc/hosts on Nautilus App 1 server requires adjustments to its Access Control Lists (ACLs) as follows:



1. The file's user owner and group owner should be set to root.

2. Others should possess read only permissions on the file.

3. User james must not have any permissions on the file.

4. User garrett should be granted read only permission on the file.

**Required configuration:**

- Server: Nautilus App 1 (`stapp01`)
- File: `/etc/hosts`
- Owner: `root`
- Group: `root`
- Others: Read-only permission
- User `james`: No permissions
- User `garrett`: Read-only permission

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `sudo su` – Switch to root user
- `chown` – Change file ownership
- `chmod` – Change file permissions
- `setfacl` – Configure Access Control Lists
- `getfacl` – Verify ACL permissions

## 3. Implementation Steps

### Step 1: Connect to Nautilus App 1

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

### Step 4: Check Existing File Permissions

```bash
ls -l /etc/hosts
```

Check the current ownership and permissions before making changes.

### Step 5: Set Owner and Group to Root

Run:

```bash
chown root:root /etc/hosts
```

This sets both the file owner and group owner to `root`.

### Step 6: Give Others Read-Only Permission

Run:

```bash
chmod o=r /etc/hosts
```

This gives users outside the owner and group read-only permission.

### Step 7: Configure ACL for User James

Run:

```bash
setfacl -m u:james:--- /etc/hosts
```

This removes all file permissions from user `james`.

### Step 8: Configure ACL for User Garrett

Run:

```bash
setfacl -m u:garrett:r-- /etc/hosts
```

This grants read-only permission to user `garrett`.

### Step 9: Verify the Final Permissions

Check the file ownership and basic permissions:

```bash
ls -l /etc/hosts
```

Check the detailed ACL configuration:

```bash
getfacl /etc/hosts
```

The ACL output should confirm:

- Owner is `root`.
- Group is `root`.
- User `james` has no permissions.
- User `garrett` has read-only permission.
- Others have read-only permission.

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh tony@<APP_SERVER_1_IP>` | Connect to Nautilus App 1 |
| `sudo su` | Switch to root user |
| `hostname` | Verify the server |
| `ls -l /etc/hosts` | Check file ownership and permissions |
| `chown root:root /etc/hosts` | Set owner and group to root |
| `chmod o=r /etc/hosts` | Give others read-only permission |
| `setfacl -m u:james:--- /etc/hosts` | Remove all ACL permissions for james |
| `setfacl -m u:garrett:r-- /etc/hosts` | Give garrett read-only ACL permission |
| `getfacl /etc/hosts` | Verify detailed ACL permissions |

**Important command explanation:**

- `chown` – Changes file ownership.
- `root:root` – Sets the owner and group to root.
- `chmod` – Changes file permissions.
- `o` – Represents others.
- `=` – Sets the specified permissions exactly.
- `setfacl` – Adds or modifies ACL entries.
- `-m` – Modifies an existing ACL or adds a new entry.
- `u:james:---` – Gives james no permissions.
- `u:garrett:r--` – Gives garrett read-only permission.
- `getfacl` – Displays detailed ACL information.

## 5. Final Result

The required configuration is:

| Details | Required Permission |
|---|---|
| File | `/etc/hosts` |
| Owner | `root` |
| Group | `root` |
| Others | Read only (`r--`) |
| User `james` | No permissions (`---`) |
| User `garrett` | Read only (`r--`) |

The task is complete once `getfacl /etc/hosts` confirms the required ownership and ACL entries.

## 6. What I Learned

- How to change file ownership using `chown`.
- How to manage basic Linux permissions using `chmod`.
- What Access Control Lists (ACLs) are.
- How to give specific permissions to individual users.
- How to remove all permissions from a particular user.
- How to verify ACL entries using `getfacl`.

## 7. Real-World Use Case in IT Companies

In IT companies, multiple users may need different levels of access to the same configuration file.

For example, a system administrator may need full access, one developer may need read-only access, and another user may not need access at all.

Instead of changing permissions for everyone, administrators can use ACLs to assign permissions to individual users.

This helps manage access to important Linux configuration files more precisely.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** File Permissions and ACL Management  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing Nautilus App 1 identification, file ownership changes, ACL configuration for james and garrett, and final permission verification using `getfacl`.

<img width="684" height="353" alt="t1" src="https://github.com/user-attachments/assets/3c9ddd99-ed7b-4413-8167-fce944c01b5a" />

<img width="671" height="70" alt="t2" src="https://github.com/user-attachments/assets/8724064f-3450-48ee-bfe6-c3e297936467" />

<img width="727" height="421" alt="t3" src="https://github.com/user-attachments/assets/3e998777-b602-490c-8ef9-4ea09f9c735f" />

<img width="757" height="464" alt="t4" src="https://github.com/user-attachments/assets/61968627-a4d1-40bc-9342-88640fe378a1" />



