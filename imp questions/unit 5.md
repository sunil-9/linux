## 1. Explain the procedure of adding, removing and modifying user accounts in Linux with necessary commands and examples.
Managing user accounts in Linux involves adding, removing, and modifying user accounts. Here's a step-by-step procedure for performing these tasks using necessary commands and examples:

**Adding a User Account:**

1. To add a user account, you can use the `useradd` command. For example, to add a user named "john," you would run:

   ```bash
   sudo useradd john
   ```

   This creates a new user without specifying any additional options. The user will be created with default settings, including a home directory under `/home/john`.

2. To set a password for the new user, use the `passwd` command:

   ```bash
   sudo passwd john
   ```

   You will be prompted to enter and confirm the password for the user.

3. Optionally, you can specify additional options while creating the user. For instance, to set the user's home directory and specify their shell, you can use the `-d` and `-s` options:

   ```bash
   sudo useradd -d /home/john -s /bin/bash john
   ```

**Modifying User Account Properties:**

1. To modify user account properties, you can use the `usermod` command. For example, to change the user "john" to use the `/bin/bash` shell, run:

   ```bash
   sudo usermod -s /bin/bash john
   ```

2. To change the user's home directory, use the `-d` option:

   ```bash
   sudo usermod -d /new/home/directory john
   ```

3. You can also modify other user attributes using `usermod`, such as changing the user's primary group with the `-g` option or adding the user to additional groups with the `-aG` option.

**Removing a User Account:**

1. To remove a user account, use the `userdel` command followed by the username:

   ```bash
   sudo userdel john
   ```

   By default, `userdel` only removes the user account and not the user's home directory and files. To remove the user's home directory as well, use the `-r` option:

   ```bash
   sudo userdel -r john
   ```

**Viewing User Account Information:**

1. To view user account information, you can use the `id` command:

   ```bash
   id john
   ```


## 2. What do you means by disk quota? Write the steps of setting user disk quotas.Write the process of implementing Disk Quata in Linux.
**Disk Quotas** in Linux are a system for limiting the amount of disk space or the number of inodes that a user or a group of users can consume on a filesystem. This feature is useful in multi-user environments and on systems where you want to prevent users from using excessive disk resources.

Here are the steps to set user disk quotas and implement disk quotas in Linux:

**Step 1: Check Kernel Support for Quotas:**

Before enabling disk quotas, ensure that your Linux kernel supports quota features. Most modern kernels have quota support built-in. You can check if quotas are supported by examining the `/proc/mounts` file:

```bash
cat /proc/mounts | grep usrquota
cat /proc/mounts | grep grpquota
```

If you see output lines containing `usrquota` or `grpquota`, your kernel supports user and group quotas.

**Step 2: Prepare the Filesystem:**

You need to enable quota support on the filesystem where you want to enforce quotas. Typically, this is your user's home directory filesystem. Edit the `/etc/fstab` file to include the `usrquota` and `grpquota` options for the corresponding filesystem. For example:

```bash
/dev/sda1 /home ext4 defaults,usrquota,grpquota 0 0
```

After editing, remount the filesystem:

```bash
mount -o remount /home
```

**Step 3: Install Quota Tools:**

Ensure that the quota tools are installed on your system. If not, install them using your package manager. For example, on Debian/Ubuntu-based systems:

```bash
sudo apt-get install quota
```

**Step 4: Initialize Quota Database:**

Run the `quotacheck` command to initialize the quota database for the specified filesystem. Replace `/home` with the path to the filesystem you want to enable quotas on:

```bash
sudo quotacheck -cug /home
```

**Step 5: Enable Quotas:**

Enable quotas for the filesystem using the `quotaon` command:

```bash
sudo quotaon /home
```

**Step 6: Set User and Group Quotas:**

Use the `edquota` command to set user and group quotas. For example, to set user "john" with a soft limit of 1GB and a hard limit of 2GB on the `/home` filesystem:

```bash
sudo edquota -u john
```

This command will open an editor (usually `nano` or `vi`) where you can set the quota values.

**Step 7: Check Quota Usage:**

You can check the current quota usage for a user or group using the `quota` command:

```bash
quota -u john
```

**Step 8: Monitoring and Maintenance:**

To regularly check and update quotas, you can set up a cron job to run `quotacheck` and `quotaon` at specified intervals.

## 3. Explain the following user management commands with example of each.
```
useradd, usermod, groupadd, userdel 
```
**1. `useradd`:**
   - The `useradd` command is used to create a new user account on a Linux system.
   - Example: To create a new user named "jane," you would run:

     ```bash
     sudo useradd jane
     ```

     This command creates the user "jane" with default settings, including a home directory.

**2. `usermod`:**
   - The `usermod` command is used to modify user account properties, such as changing the user's home directory or shell.
   - Example: To change the shell for the user "jane" to `/bin/bash`, you would run:

     ```bash
     sudo usermod -s /bin/bash jane
     ```

     This command modifies the user's shell to `/bin/bash`.

**3. `groupadd`:**
   - The `groupadd` command is used to create a new group on the system.
   - Example: To create a new group named "developers," you would run:

     ```bash
     sudo groupadd developers
     ```

     This command creates the group "developers."

**4. `userdel`:**
   - The `userdel` command is used to remove a user account from the system. By default, it only removes the user account, not the user's home directory or files.
   - Example: To remove the user "jane," you would run:

     ```bash
     sudo userdel jane
     ```

     This command removes the user account "jane."

   - To remove the user account along with the user's home directory and files, use the `-r` option:

     ```bash
     sudo userdel -r jane
     ```

     This command removes the user account "jane" and deletes their home directory and files.

## 4. Write the command Syntax for the following purpose
```
i) To create a user “Linux” with password “redhat”
ii) To change the password for that user to “fedora”
iii) To create a group “Hackers”
iv) After all assign the group “Hackers” for the user "“Linux”
V) After all provide comment name “Blackcat” and login shell “bash” for that user.
vi) Then assign the expiry date for that user account.
vii) To delete that group
viii) To remove that user
```


**i) To create a user "Linux" with password "redhat":**
```bash
sudo useradd Linux -p $(openssl passwd -1 redhat)
```

**ii) To change the password for that user to "fedora":**
```bash
sudo passwd Linux
```

**iii) To create a group "Hackers":**
```bash
sudo groupadd Hackers
```

**iv) After all, assign the group "Hackers" for the user "Linux":**
```bash
sudo usermod -aG Hackers Linux
```

**V) After all, provide the comment name "Blackcat" and login shell "bash" for that user:**
```bash
sudo usermod -c "Blackcat" -s /bin/bash Linux
```

**vi) Then assign the expiry date for that user account:**
```bash
sudo chage -E YYYY-MM-DD Linux
```
Replace `YYYY-MM-DD` with the desired expiration date.

**vii) To delete that group:**
```bash
sudo groupdel Hackers
```

**viii) To remove that user:**
```bash
sudo userdel -r Linux
```