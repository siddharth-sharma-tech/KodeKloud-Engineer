# Task 01: Custom Apache User Setup

## 1. Problem Statement

In response to heightened security concerns, the xFusionCorp Industries security team has opted for custom Apache users for their web applications. Each user is tailored specifically for an application, enhancing security measures. Your task is to create a custom Apache user according to the outlined specifications:



a. Create a user named ammar on App server 2 within the Stratos Datacenter.


b. Assign a unique UID 1779 and designate the home directory as /var/www/ammar.

## 2. Tools & Technologies Used

- **Linux:** Operating system
- **SSH:** To connect to the application server
- **Linux CLI:** To execute commands
- **useradd:** To create the Linux user
- **id, getent, ls:** To verify the user and home directory

## 3. Implementation Steps

### Step 1: Connect to App Server 2

From the jump host, connect to App Server 2 using its SSH login username, `steve`.

```bash
ssh steve@stapp02
```

### Step 2: Switch to Root User

After connecting, switch to the root user.

```bash
sudo su
```

### Step 3: Verify the Server

Check the hostname to make sure you are working on the correct server.

```bash
hostname
```

Expected hostname:

```text
stapp02
```

### Step 4: Create the User

Create the user `ammar` with UID `1779` and home directory `/var/www/ammar`.

```bash
useradd -u 1779 -d /var/www/ammar -m ammar
```

### Step 5: Verify the User

Check whether the user was created with the correct UID.

```bash
id ammar
```

Check the user's account details.

```bash
getent passwd ammar
```

Check whether the home directory exists.

```bash
ls -ld /var/www/ammar
```

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh steve@<APP_SERVER_2_IP>` | Connect to App Server 2 |
| `sudo su` | Switch to the root user |
| `hostname` | Verify the server hostname |
| `useradd -u 1779 -d /var/www/ammar -m ammar` | Create the user with a custom UID and home directory |
| `id ammar` | Check the user's UID and groups |
| `getent passwd ammar` | Display the user's account information |
| `ls -ld /var/www/ammar` | Verify the home directory |

**Command explanation:**
- useradd – Creates a new Linux user.
- `-u 1779` – Assigns UID 1779 to the user.
- `-d /var/www/ammar` – Sets the home directory.
- `-m` – Creates the home directory if it does not exist.
- `ammar` – Name of the new user.

## 5. Final Result

The task requires the following configuration on App Server 2:

| Details | Value |
|---|---|
| Server | `stapp02` |
| Username | `ammar` |
| UID | `1779` |
| Home Directory | `/var/www/ammar` |

The task is complete once the verification commands confirm the correct UID and home directory.

## 6. What I Learned

- How to connect to a Linux server using SSH.
- How to switch to the root user using `sudo su`.
- How to create a Linux user with a specific UID.
- How to assign a custom home directory.
- How to verify user details using `id` and `getent`.
- How to check whether a user's home directory exists.

## 7. Real-World Use Case in IT Companies

In IT companies, different applications may use separate Linux user accounts on the same server.

For example, an Apache application can have its own dedicated user instead of sharing an account with other applications.

This helps administrators manage file ownership and control which users can access application files. Additional permissions and Apache configuration are needed to enforce the required access restrictions.

This task demonstrates a basic Linux user-management practice used by system and DevOps engineers.

## 8. Practical Experience

Learning Platform: KodeKloud
Category: Linux Administration
Topic: User Management
Difficulty: Beginner

Evidence: Terminal screenshots showing server identification, user creation and successful verification.

<img width="578" height="296" alt="t1" src="https://github.com/user-attachments/assets/52eb4c8d-ca09-42ff-a906-dbb778776ec5" />
<img width="584" height="53" alt="t2" src="https://github.com/user-attachments/assets/64e01eed-989b-4c5e-91e9-33183c7f2c59" />
<img width="571" height="133" alt="t3" src="https://github.com/user-attachments/assets/2b5a4e67-1709-4f7c-a15e-98ee4a491fd8" />
<img width="825" height="359" alt="t4" src="https://github.com/user-attachments/assets/fc786eae-d043-42b3-9df2-0ba276141c74" />

