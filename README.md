# PP4

## Goal

In this exercise you will:

* Use SSH to connect to remote servers from WSL, macOS, or Linux shells, understanding the handshake and authentication process.
* Generate an Ed25519 SSH key pair and explain the concept of digital signatures.
* Configure your local SSH client via the `~/.ssh/config` file for streamlined access.
* Securely copy files between local and remote hosts using `scp`, including local-to-remote, remote-to-local, and remote-to-remote transfers.
* Automate startup tasks on the remote server by writing a shell script that runs at login and explaining the role of `~/.bashrc` vs. `~/.profile`.

**Important:** Start a stopwatch when you begin and work uninterruptedly for **90 minutes**. Once time is up, stop immediately and record exactly where you paused.

---

## Workflow

1. **Fork** this repository
2. **Modify & commit** your solution
3. **Submit your link for Review**

---

## Prerequisites

* Several starter repos are available here:
  [https://github.com/orgs/STEMgraph/repositories?q=SSH%3A](https://github.com/orgs/STEMgraph/repositories?q=SSH%3A)
* Consult the SSH and SCP man-pages for detailed options and explanations:

  * `man ssh`
  * `man scp`

---

## Tasks

### Task 1: SSH Login

**Objective:** Establish an SSH connection and observe each stage of the process.

1. From your local shell (WSL, macOS Terminal, or Linux), log into the `vorlesungsserver` (or any other remote machine of your choice, e.g. your own raspberry pi):

   ```bash
   ssh youruser@remotehost
   ```
2. Carefully observe and note each step:

   * **TCP connection** to port 22 on `remotehost`.
   * **SSH protocol handshake**: key exchange and algorithm negotiation.
   * **Authentication**: public-key or password exchange.
   * **Shell allocation**: your remote session starts.
3. After login, exit the session with `exit`.

**Provide:**

```bash
# 1) The exact ssh command you ran
ssh user11@128.140.85.215 -v

# 2) A detailed, step-by-step explanation of what happened at each stage
OpenSSH_9.6p1 Ubuntu-3ubuntu13.5, OpenSSL 3.0.13 30 Jan 2024
debug1: Reading configuration data /home/eugen/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no files
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug1: Connecting to 128.140.85.215 [128.140.85.215] port 22.
debug1: Connection established.
debug1: identity file /home/eugen/.ssh/id_rsa type -1
debug1: identity file /home/eugen/.ssh/id_rsa-cert type -1
debug1: identity file /home/eugen/.ssh/id_ecdsa type -1
debug1: identity file /home/eugen/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/eugen/.ssh/id_ecdsa_sk type -1
debug1: identity file /home/eugen/.ssh/id_ecdsa_sk-cert type -1
debug1: identity file /home/eugen/.ssh/id_ed25519 type 3
debug1: identity file /home/eugen/.ssh/id_ed25519-cert type -1
debug1: identity file /home/eugen/.ssh/id_ed25519_sk type -1
debug1: identity file /home/eugen/.ssh/id_ed25519_sk-cert type -1
debug1: identity file /home/eugen/.ssh/id_xmss type -1
debug1: identity file /home/eugen/.ssh/id_xmss-cert type -1
debug1: identity file /home/eugen/.ssh/id_dsa type -1
debug1: identity file /home/eugen/.ssh/id_dsa-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_9.6p1 Ubuntu-3ubuntu13.5
debug1: Remote protocol version 2.0, remote software version OpenSSH_9.2p1 Debian-2+deb12u5
debug1: compat_banner: match: OpenSSH_9.2p1 Debian-2+deb12u5 pat OpenSSH* compat 0x04000000
debug1: Authenticating to 128.140.85.215:22 as 'user11'
debug1: load_hostkeys: fopen /home/eugen/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: algorithm: sntrup761x25519-sha512@openssh.com
debug1: kex: host key algorithm: ssh-ed25519
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: SSH2_MSG_KEX_ECDH_REPLY received
debug1: Server host key: ssh-ed25519 SHA256:RxMwhpDxDq2aHcMAnAUsHJmeWgVVmCkXQSJCkB8zu44
debug1: load_hostkeys: fopen /home/eugen/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug1: Host '128.140.85.215' is known and matches the ED25519 host key.
debug1: Found key in /home/eugen/.ssh/known_hosts:1
debug1: ssh_packet_send2_wrapped: resetting send seqnr 3
debug1: rekey out after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: ssh_packet_read_poll2: resetting read seqnr 3
debug1: SSH2_MSG_NEWKEYS received
debug1: rekey in after 134217728 blocks
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_ext_info_client_parse: server-sig-algs=<ssh-ed25519,sk-ssh-ed25519@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ecdsa-sha2-nistp256@openssh.com,webauthn-sk-ecdsa-sha2-nistp256@openssh.com,ssh-dss,ssh-rsa,rsa-sha2-256,rsa-sha2-512>
debug1: kex_ext_info_check_ver: publickey-hostbound@openssh.com=<0>
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Will attempt key: /home/eugen/.ssh/id_rsa
debug1: Will attempt key: /home/eugen/.ssh/id_ecdsa
debug1: Will attempt key: /home/eugen/.ssh/id_ecdsa_sk
debug1: Will attempt key: /home/eugen/.ssh/id_ed25519 ED25519 SHA256:cof1I0yCklbyEksi97mFTEex71Noc8gPAnfywRCzgSM
debug1: Will attempt key: /home/eugen/.ssh/id_ed25519_sk
debug1: Will attempt key: /home/eugen/.ssh/id_xmss
debug1: Will attempt key: /home/eugen/.ssh/id_dsa
debug1: Trying private key: /home/eugen/.ssh/id_rsa
debug1: Trying private key: /home/eugen/.ssh/id_ecdsa
debug1: Trying private key: /home/eugen/.ssh/id_ecdsa_sk
debug1: Offering public key: /home/eugen/.ssh/id_ed25519 ED25519 SHA256:cof1I0yCklbyEksi97mFTEex71Noc8gPAnfywRCzgSM
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/eugen/.ssh/id_ed25519_sk
debug1: Trying private key: /home/eugen/.ssh/id_xmss
debug1: Trying private key: /home/eugen/.ssh/id_dsa
debug1: Next authentication method: password
user11@128.140.85.215's password:
Authenticated to 128.140.85.215 ([128.140.85.215]:22) using "password".
debug1: channel 0: new session [client-session] (inactive timeout: 0)
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: pledge: filesystem
debug1: client_input_global_request: rtype hostkeys-00@openssh.com want_reply 0
debug1: client_input_hostkeys: searching /home/eugen/.ssh/known_hosts for 128.140.85.215 / (none)
debug1: client_input_hostkeys: searching /home/eugen/.ssh/known_hosts2 for 128.140.85.215 / (none)
debug1: client_input_hostkeys: hostkeys file /home/eugen/.ssh/known_hosts2 does not existdebug1: client_input_hostkeys: no new or deprecated keys from server
debug1: Sending environment.
debug1: channel 0: setting env LANG = "C.UTF-8"
debug1: pledge: fork
Linux vorlesung 6.1.0-21-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.90-1 (2024-05-03) x86_64
The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Thu May 15 15:25:39 2025 from 195.37.6.6

---

### Task 2: Ed25519 Key Pair

**Objective:** Create a secure key pair and explain how digital signatures verify identity.

1. Generate an Ed25519 SSH key pair:

   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   * Accept the default file location (`~/.ssh/id_ed25519`). Or provide the `-f <filepath>` option additionally.
   * Enter a passphrase when prompted (optional).
2. Locate and inspect your `id_ed25519` (private key) and `id_ed25519.pub` (public key).
3. Install your key on the remote machine (e.g. `vorlesungsserver`.
4. Explain in writing:

   * How the **private key** is used to sign challenges.
   * How the **public key** on the server verifies signatures without revealing the private key.
   * Why Ed25519 is preferred (performance, security).

**Provide:**

```bash
# 1) The ssh-keygen command you ran
ssh-keygen -t ed25519 -C "eugen.risling@stud.thga.de"

# 2) The file paths of the generated keys
/home/eugen/.ssh/id_ed25519
/home/eugen/.ssh/id_ed25519.pub

# 3) Your written explanation (3–5 sentences) of the signature process
The command creates a key pair (private and public). This is done in the ed25519 code.
You'll be asked for the storage location and whether you want to enter a passphrase.
The key is then created. The key consists of numbers and digits, such as the email address.
 A random art image is also created.

---

### Task 3: SSH Config File

**Objective:** Simplify SSH commands via `~/.ssh/config`.

1. Open (or create) `~/.ssh/config` in `vim`.
2. Add entries for your hosts, for example:

   ```text
   Host my-remote
       HostName remote.example.com
       User youruser
       IdentityFile ~/.ssh/id_ed25519

   Host backup-server
       HostName backup.example.com
       User backupuser
       Port 2222
       IdentityFile ~/.ssh/id_ed25519_backup
   ```
3. Save and close the file, then test:

   ```bash
   ssh my-remote
   ssh backup-server
   ```
4. Explain:

   * How SSH reads `~/.ssh/config` and matches hosts.
     The name is searched for.
   * The difference between `HostName` and `Host`.
     Hostname is the name for a computer in a network, a host is just a aliases name.
   * How aliases prevent long commands.
     The aliases are shortcuts for long commands.

**Provide:**

```text
# 1) The full contents of your ~/.ssh/config
Host my-remote
               HostName remote.example.com
               User eugen
               IdentityFile ~/.ssh/id_ed25519

# 2) A short explanation (3–4 sentences) of how the config simplifies connections
The SSH file stores the parameters necessary for connecting to a host.
For example, the path to the SSH key is stored here.
It also contains information about the username, host address, and port.
This file eliminates the need to enter anything separately when connecting;
it is read automatically from the config file.

---

### Task 4: SCP File Transfers

**Objective:** Practice copying files securely using `scp`.

1. **Local → Remote**:

   ```bash
   scp /path/to/localfile.txt youruser@remotehost:~/destination/
   ```
2. **Remote → Local**:

   ```bash
   scp youruser@remotehost:~/remotefile.log ./local_destination/
   ```
3. **Remote → Remote** (between two directories on the same remote host):

   ```bash
   scp -r youruser@remotehost:/path/dir1 youruser@remotehost:/path/dir2
   ```
4. For each command:

   * Verify file timestamps and sizes after transfer, using `ls -la`
  user11@vorlesung:~$ ls -la
total 36
drwx------   3 user11 user11 4096 May 17 14:17 .
drwxr-xr-x 161 root   root   4096 Apr 20 16:35 ..
-rw-------   1 user11 user11   28 May 17 14:01 .bash_history
-rw-r--r--   1 user11 user11  220 Apr  2 12:56 .bash_logout
-rw-r--r--   1 user11 user11 3526 Apr  2 12:56 .bashrc
-rw-r--r--   1 user11 user11    0 Apr  2 12:56 .cloud-locale-test.skip
drwxr-xr-x   2 user11 user11 4096 May 17 14:00 eugen
-rw-r--r--   1 user11 user11   37 May 17 14:17 eugen1.txt
-rw-r--r--   1 user11 user11  807 Apr  2 12:56 .profile
-rw-------   1 user11 user11  795 May 17 14:17 .viminfo


eugen@User-PC:~$ ls -la
total 76
drwxr-x--- 1 eugen eugen   512 May 17 16:20 .
drwxr-xr-x 1 root  root    512 Apr  3 17:54 ..
-rw------- 1 eugen eugen  2920 May 15 17:53 .bash_history
-rw-r--r-- 1 eugen eugen   220 Apr  3 17:54 .bash_logout
-rw-r--r-- 1 eugen eugen  3771 Apr  3 17:54 .bashrc
-rw------- 1 eugen eugen 12288 May  1 16:13 .eugen2.txt.swp
-rw-r--r-- 1 eugen eugen    62 May 13 12:59 .gitconfig
drwxr-xr-x 1 eugen eugen   512 Apr  3 17:56 .landscape
-rw-r--r-- 1 eugen eugen     0 May 17 15:50 .motd_shown
-rw-r--r-- 1 eugen eugen   807 Apr  3 17:54 .profile
drwxr-xr-x 1 eugen eugen   512 May 15 17:24 .ssh
-rw-r--r-- 1 eugen eugen     0 Apr 28 22:22 .sudo_as_admin_successful
-rw------- 1 eugen eugen 12502 May 14 21:06 .viminfo
-rw-r--r-- 1 eugen eugen 33583 May  1 19:31 TEST
-rw-r--r-- 1 eugen eugen    35 May  1 16:10 eugen1.txt
-rw-r--r-- 1 eugen eugen    25 May  1 16:23 eugen2.txt
-rw-r--r-- 1 eugen eugen    32 May  1 16:28 eugen3.txt
-rw-r--r-- 1 eugen eugen   386 Apr 30 19:47 example.svg
-rw-r--r-- 1 eugen eugen   215 Apr 16 20:36 function
-rw-r--r-- 1 eugen eugen   434 Apr 16 20:36 functions
-rw-r--r-- 1 eugen eugen    37 May 17 16:20 lokal
drwxr-xr-x 1 eugen eugen   512 Apr 17 18:33 projekt1
-rw-r--r-- 1 eugen eugen   221 Apr 21 17:04 test
   * 
   * Note any flags you used (e.g., `-r`, `-P` for port).
4. Explain:

   * How `scp` initiates an SSH session for each transfer.
   * The role of encryption in protecting data in transit.

**Provide:**

```bash
# 1) Each scp command you ran
scp ~/eugen1.txt user11@128.140.85.215:~/

scp user11@128.140.85.215:/home/user11/eugen1.txt ./lokal

# 2) Any flags or options used
No options used.
# 3) A brief explanation (2–3 sentences) of scp’s mechanism
SCP is a service for copying files to and from a remote host and back to the local PC over a secure SSH connection.
A password must be entered for each operation.

---

### Task 5: Login Shell Script & Profile Explanation

**Objective:** Automate commands at login and understand shell initialization files.

1. On the **remote** server, create a script `~/login_tasks.sh` containing at least three commands you find useful (e.g., `echo "Welcome $(whoami)"`, `uptime`, `ls ~/projects`). You may either use `vim` or try the following to create a file from your commandline directely:

   ```bash
   cat << 'EOF' > ~/login_tasks.sh
   #!/usr/bin/env bash
   echo "Welcome $(whoami)! Today is $(date)."
   uptime
   ls ~/projects
   EOF
   chmod +x ~/login_tasks.sh
   ```

> The files content should be something akin to:
> ```bash
> #!/usr/bin/env bash
> echo "Welcome $(whoami)! Today is $(date)."
> uptime
> ls ~/projects
> ```

2. Append to your `~/.bashrc` (or `~/.profile` if using a login shell) a line to source this script on each new session:

   ```bash
   echo "source ~/login_tasks.sh" >> ~/.bashrc
   ```
3. Log out and log back in to trigger the script.
4. Explain:

   * The difference between `~/.bashrc` and `~/.profile` (interactive vs. login shells).
   * Why and when each file is read.
   * How sourcing differs from executing.

**Provide:**

```bash
# 1) The contents of login_tasks.sh
# 2) The lines you added to ~/.bashrc or ~/.profile
# 3) Your explanation (3–5 sentences) of shell init files and sourcing vs. executing
```

---

**Remember:** Stop working after **90 minutes** and record where you stopped.
