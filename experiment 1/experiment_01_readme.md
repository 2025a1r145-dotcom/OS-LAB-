<img width="1179" height="582" alt="Screenshot 2026-11-16 at 10 26 06 PM" src="https://github.com/user-attachments/assets/0fc61003-612c-457f-b4be-739cb08468bb" />
<img width="1127" height="562" alt="Screenshot 2026-11-16 at 10 26 02 PM" src="https://github.com/user-attachments/assets/3ce9d31f-ddad-4b6f-a413-71abf77cfe25" />
<img width="1095" height="535" alt="Screenshot 2026-11-16 at 10 25 56 PM" src="https://github.com/user-attachments/assets/11972e8f-cbf3-4cb7-9323-21cfaf31d415" />
<img width="1242" height="581" alt="Screenshot 2026-11-16 at 10 25 50 PM" src="https://github.com/user-attachments/assets/9d4b1f9d-ce3b-4201-b499-310610f98e8a" />
<img width="1110" height="536" alt="Screenshot 2026-11-16 at 10 25 45 PM" src="https://github.com/user-attachments/assets/741cf86a-a33d-4662-8479-edc7aecad01d" />
<img width="1455" height="550" alt="Screenshot 2026-11-16 at 10 25 36 PM" src="https://github.com/user-attachments/assets/8fdff3b2-e5b3-4a33-bf64-bdea22f19678" />
<img width="1125" height="559" alt="Screenshot 2026-11-16 at 10 25 30 PM" src="https://github.com/user-attachments/assets/6edfca3d-1fba-4f8d-b029-c81e3b73e5d4" />
# Experiment 01: Installation and Configuration of Oracle VirtualBox and Ubuntu Linux

## Aim
To install Oracle VirtualBox, create and configure a virtual machine, and install Ubuntu Linux in a virtualized environment.

---

## Requirements
* **Hardware:** Computer or laptop with sufficient RAM and disk space
* **Software:** Oracle VirtualBox
* **OS Image:** Ubuntu Linux ISO image

---

## Procedure
1. Download **Oracle VirtualBox** from its official website and complete the installation.
2. Download the **Ubuntu Linux ISO** image from the official Ubuntu website.
3. Open Oracle VirtualBox and click on **New**.
4. Enter the virtual machine name as `Ubuntu Linux`.
5. Allocate the required amount of RAM and create a virtual hard disk.
6. Attach the downloaded Ubuntu ISO image to the virtual machine's optical drive.
7. Start the virtual machine and follow the on-screen installation instructions.
8. Restart the virtual machine once the installation is complete.

---

## Verification

Run the following commands in the Ubuntu terminal to verify the installation:

```bash
uname -a
cat /etc/os-release
```

### Expected Output
* `uname -a`: Displays the Linux kernel information.
* `cat /etc/os-release`: Displays the installed operating system version and details.

---

## Basic Linux Commands Executed

1. **Display Linux system information:**
   ```bash
   uname -a
   ```
2. **Display Ubuntu version and details:**
   ```bash
   cat /etc/os-release
   ```
3. **Display current date and time:**
   ```bash
   date
   ```
4. **Display the current logged-in user:**
   ```bash
   whoami
   ```
5. **Display the current working directory:**
   ```bash
   pwd
   ```
6. **Display CPU information:**
   ```bash
   lscpu
   ```
7. **Display memory usage:**
   ```bash
   free -h
   ```
8. **Display disk space:**
   ```bash
   df -h
   ```
9. **Display IP address information:**
   ```bash
   ip addr
   ```
10. **Display the Ubuntu kernel version:**
    ```bash
    uname -r
    ```

---

## Result
Oracle VirtualBox and Ubuntu Linux have been successfully installed, configured, and verified in a virtualized environment.
