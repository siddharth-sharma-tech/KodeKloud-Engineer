# Task 02: Group Creation and User Assignment


## 1. Problem Statement
The system admin team at xFusionCorp Industries has streamlined access management by implementing group-based access control. Here's what you need to do:



a. Create a group named nautilus_developers across all App servers within the Stratos Datacenter.


b. Add the user jarod into the nautilus_developers group on all App servers. If the user doesn't exist, create it as well.

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `groupadd` – Create a group
- `useradd` – Create a user
- `usermod` – Add a user to a group
- `id` and `getent` – Verify users and groups

## 3. Implementation Steps

I performed the same configuration on all three App Servers.

### Step 1: Connect to App Server 1

From the jump host, connect using the server login username.

```bash
ssh tony@stapp01
```

Switch to the root user:

```bash
sudo su
```

Verify the hostname:

```bash
hostname
```

Expected hostname: `stapp01`

### Step 2: Create the Group

Create the group `nautilus_developers`.

```bash
groupadd nautilus_developers
```

### Step 3: Check Whether the User Exists

```bash
id jarod
```

If the user does not exist, create it:

```bash
useradd jarod
```

If `id jarod` displays the user's details, the user already exists, so there is no need to create it again.

### Step 4: Add the User to the Group

```bash
usermod -aG nautilus_developers jarod
```

### Step 5: Repeat on App Server 2

Connect to App Server 2:

```bash
ssh steve@stapp02
```

Switch to root:

```bash
sudo su
```

Verify the hostname:

```bash
hostname
```

Expected hostname: `stapp02`

Repeat the group creation, user existence check, user creation if needed, and group membership commands.

### Step 6: Repeat on App Server 3

Connect to App Server 3:

```bash
ssh banner@stapp03
```

Switch to root:

```bash
sudo su
```

Verify the hostname:

```bash
hostname
```

Expected hostname: `stapp03`

Repeat the same configuration commands.

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh` | Connect to an App Server |
| `sudo su` | Switch to the root user |
| `hostname` | Check the server hostname |
| `groupadd nautilus_developers` | Create the required group |
| `id jarod` | Check whether the user exists |
| `useradd jarod` | Create the user if it does not exist |
| `usermod -aG nautilus_developers jarod` | Add the user to the group |
| `getent group nautilus_developers` | Verify group membership |

**Important command explanation:**

- `-a` – Append the group without removing existing supplementary groups.
- `-G` – Specify the supplementary group.
- `jarod` – The user being added to the group.

## 5. Final Result

The required configuration on all three App Servers is:

| Server | Group | User |
|---|---|---|
| `stapp01` | `nautilus_developers` | `jarod` |
| `stapp02` | `nautilus_developers` | `jarod` |
| `stapp03` | `nautilus_developers` | `jarod` |

To verify the configuration on each server, run:

```bash
id jarod
```

```bash
getent group nautilus_developers
```

The task is complete once both commands confirm that `jarod` belongs to `nautilus_developers` on all three servers.

## 6. What I Learned

- How to create Linux groups.
- How to check whether a user already exists.
- How to create a user when it is missing.
- How to add a user to a supplementary group.
- How to manage users and groups across multiple Linux servers.
- How to verify group membership.

## 7. Real-World Use Case in IT Companies

In IT companies, multiple developers often need access to the same application files or directories.

Instead of giving permissions to every developer individually, system administrators can create a common Linux group and add the required users to it.

For example, a group named `nautilus_developers` can contain all developers who need access to a particular project.

Administrators can then assign directory permissions to that group. This makes access management easier, especially when developers join or leave a project.

This is a common Linux administration practice used to manage access across teams.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** Group Management  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing server identification, group creation, user creation (if required), and successful group membership verification on all three App Servers.



<img width="702" height="394" alt="t1" src="https://github.com/user-attachments/assets/7687235c-a3b1-4574-a2a3-c36dcd6e4ece" />
<img width="691" height="200" alt="t2" src="https://github.com/user-attachments/assets/7483cb85-6654-4fd8-9976-bb0afa470280" />
<img width="716" height="395" alt="t3" src="https://github.com/user-attachments/assets/fb515cf8-ee00-4efa-8d00-914b11784358" />
<img width="710" height="201" alt="t4" src="https://github.com/user-attachments/assets/0d44402b-c027-41c5-98c3-2f34ff576496" />
<img width="706" height="391" alt="t5" src="https://github.com/user-attachments/assets/5202bc1f-f498-4467-9a6c-5cc95b799738" />
<img width="698" height="204" alt="t6" src="https://github.com/user-attachments/assets/6db5360a-acd2-4004-9c1e-187f8e9c7a88" />
<img width="769" height="462" alt="t7" src="https://github.com/user-attachments/assets/33488e94-7ae0-47b0-a444-67b080f75f30" />





