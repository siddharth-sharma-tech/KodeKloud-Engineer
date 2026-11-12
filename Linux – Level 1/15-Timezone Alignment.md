# Task 21: Timezone Alignmen

## 1. Problem Statement

In the daily standup, it was noted that the timezone settings across the Nautilus Application Servers in the Stratos Datacenter are inconsistent with the local datacenter's timezone, currently set to Africa/Ceuta.



Synchronize the timezone settings to match the local datacenter's timezone (Africa/Ceuta).

**Required configuration:**

- App Server 1: `stapp01`
- App Server 2: `stapp02`
- App Server 3: `stapp03`
- Required Timezone: `Africa/Ceuta`

## 2. Tools & Technologies Used

- Linux
- SSH
- Linux command line
- `sudo su` – Switch to root user
- `timedatectl` – Manage system date and timezone
- `date` – Display the current date and time
- `grep` – Check timezone availability

## 3. Implementation Steps

I performed the same configuration on all three App Servers.

### Step 1: Connect to App Server 1

Connect using the login username `tony`.

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

### Step 4: Check Available Timezones

```bash
timedatectl list-timezones | grep Africa/Ceuta
```

This checks whether the required timezone is available.

### Step 5: Check the Current Timezone

```bash
timedatectl
```

This displays the current system timezone and clock settings.

### Step 6: Set the Required Timezone

Run:

```bash
timedatectl set-timezone Africa/Ceuta
```

This changes the system timezone to `Africa/Ceuta`.

### Step 7: Verify the Timezone

```bash
timedatectl
```

You can also run:

```bash
date
```

The timezone information should now show `Africa/Ceuta` or its applicable daylight-saving abbreviation.

### Step 8: Repeat on App Server 2

Connect using `steve`.

```bash
ssh steve@stapp02
sudo su
```

Verify the hostname:

```bash
hostname
```

Expected hostname: `stapp02`

Set the timezone:

```bash
timedatectl set-timezone Africa/Ceuta
```

Verify:

```bash
timedatectl
```

### Step 9: Repeat on App Server 3

Connect using `banner`.

```bash
ssh banner@stapp03
sudo su
```

Verify the hostname:

```bash
hostname
```

Expected hostname: `stapp03`

Set the timezone:

```bash
timedatectl set-timezone Africa/Ceuta
```

Verify:

```bash
timedatectl
```

## 4. Commands Used

| Command | Purpose |
|---|---|
| `ssh` | Connect to an App Server |
| `sudo su` | Switch to root user |
| `hostname` | Verify the server |
| `timedatectl list-timezones` | List available timezones |
| `grep Africa/Ceuta` | Find the required timezone |
| `timedatectl` | Display current date and timezone settings |
| `timedatectl set-timezone Africa/Ceuta` | Change the system timezone |
| `date` | Display the current date and time |

**Important command explanation:**

- `timedatectl` – Manages system time and timezone settings.
- `list-timezones` – Displays available timezone names.
- `set-timezone` – Changes the system timezone.
- `Africa/Ceuta` – Required timezone for the datacenter.
- `date` – Displays the current system date and time.

## 5. Final Result

The required configuration is:

| Server | Required Timezone |
|---|---|
| `stapp01` | `Africa/Ceuta` |
| `stapp02` | `Africa/Ceuta` |
| `stapp03` | `Africa/Ceuta` |

The task is complete once `timedatectl` confirms `Africa/Ceuta` on all three servers.

No server reboot is required for this timezone change.

## 6. What I Learned

- How to check the current Linux timezone.
- How to list available timezones.
- How to change the timezone using `timedatectl`.
- How to verify timezone settings.
- How to configure consistent timezone settings across multiple servers.

## 7. Real-World Use Case in IT Companies

In IT companies, application servers often run in different locations.

If their timezone settings are inconsistent, application logs, scheduled jobs, and monitoring timestamps can become confusing.

System administrators configure a common timezone across servers to make log analysis, troubleshooting, and scheduled task management easier.

This is especially useful when multiple servers support the same application.

## 8. Practical Experience

**Learning Platform:** KodeKloud  
**Category:** Linux Administration  
**Topic:** Timezone Management  
**Difficulty:** Beginner

**Evidence:** Terminal screenshots showing server identification, current timezone settings, execution of the `timedatectl set-timezone` command, and final timezone verification on all three App Servers.

<img width="781" height="401" alt="t1" src="https://github.com/user-attachments/assets/378cfae6-2c32-4e77-9091-d33341bd8382" />

<img width="751" height="433" alt="t2" src="https://github.com/user-attachments/assets/f4518670-7489-41df-9ec4-8f7df704a1c4" />

<img width="733" height="401" alt="t3" src="https://github.com/user-attachments/assets/bec291d4-c732-4118-8062-65dee20b8b56" />

<img width="735" height="432" alt="t4" src="https://github.com/user-attachments/assets/c3e19fc7-229c-4acd-9aaf-fade59786da3" />

<img width="769" height="395" alt="t5" src="https://github.com/user-attachments/assets/8eeb9551-65d3-4b5f-b732-b3e36bed5a36" />

<img width="719" height="432" alt="t6" src="https://github.com/user-attachments/assets/19ee747b-f19f-4024-a737-550cbc47f320" />

<img width="763" height="473" alt="t10" src="https://github.com/user-attachments/assets/bc48e6a6-138f-4d19-8f29-bddbc7a58461" />








