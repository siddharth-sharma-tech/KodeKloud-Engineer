# Task 05: Temporary User Setup with Expiry

## 1. Problem Statement

As part of the temporary assignment to the Nautilus project, a developer named yousuf requires access for a limited duration. To ensure smooth access management, a temporary user account with an expiry date is needed. Here's what you need to do:



Create a user named rose on App Server 3 in Stratos Datacenter. Set the expiry date to 2027-01-28, ensuring the user is created in lowercase as per standard protocol.

**Required configuration:**

- Username: `rose`
- Server: App Server 3 (`stapp03`)
- Account Expiry Date: `2027-01-28`

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `useradd` – Create a Linux user
- `chage` – Manage account expiry information
- `id` and `getent` – Verify user details

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

Check that you are connected to App Server 3.

```bash
hostname
```

Expected hostname:

```text
stapp03
```

### Step 4: Create the User with an Expiry Date

Run the following command:

```bash
useradd -e 2027-01-28 rose
```

The `-e` option sets the account expiry date.

### Step 5: Verify the User

Check whether the user was created:

```bash
id rose
```

Check the user's account information:

```bash
getent passwd rose
```

Verify the account expiry date:

```bash
chage -l rose
```

Look for the account expiration date in the output. It should show `Jan 28, 2027`.

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh banner@<APP_SERVER_3_IP>` | Connect to App Server 3 |
| `sudo su` | Switch to the root user |
| `hostname` | Verify the server |
| `useradd -e 2027-01-28 rose` | Create the user with an expiry date |
| `id rose` | Verify the user |
| `getent passwd rose` | Display user account information |
| `chage -l rose` | Check account expiry information |

**Command explanation:**

- `useradd` – Creates a Linux user.
- `-e` – Sets the account expiration date.
- `2027-01-28` – Expiry date in `YYYY-MM-DD` format.
- `rose` – Username, created in lowercase.
- `chage -l` – Displays account aging and expiry information.

## 5. Final Result

The required configuration is:

| Details | Value |
|---|---|
| Server | `stapp03` |
| Username | `rose` |
| Account Expiry Date | `2027-01-28` |

The task is complete once the user exists and `chage -l rose` confirms the correct expiry date.

## 6. What I Learned

- How to create a Linux user with an expiry date.
- How to use the `-e` option with `useradd`.
- How to check account expiry using `chage`.
- How to manage temporary user accounts.
- Why temporary accounts should have a defined expiry date.

## 7. Real-World Use Case in IT Companies

In IT companies, developers and contractors sometimes need server access only for a specific project or period.

For example, a developer working temporarily on a project may need access to a Linux server for a few weeks or months.

Instead of manually remembering to remove the account later, administrators can set an expiry date when creating it. This helps prevent temporary accounts from remaining active longer than required.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** User Management  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing the connection to App Server 3, user creation, and verification of the account expiry date using `chage -l rose`.

<img width="699" height="301" alt="t5" src="https://github.com/user-attachments/assets/2d3b69cc-88fd-4c3b-aefa-2e81a7e820d6" />

<img width="631" height="70" alt="t6" src="https://github.com/user-attachments/assets/73183cc2-9a52-45a0-8702-974448db111f" />

<img width="663" height="280" alt="t7" src="https://github.com/user-attachments/assets/0a5ccaa9-33c7-44a0-83d7-4717db940e0d" />

<img width="738" height="451" alt="t8" src="https://github.com/user-attachments/assets/24d3f30b-762b-4817-8ff3-efabcabfb458" />



