<div align="center" style="display: flex; align-items: center; justify-content: center; gap: 15px;">
  <h1 style="margin: 0;">UNT CSE GitLab ENVIRONMENT SETUP GUIDE</h1>
</div>

<p align="center">
  Step-by-step guide to set up CSE GitLab and prepare a project workspace on CSE cell machines.
</p>

---


<p align="right">
- Super90 
</p>

---

## Overview

This guide walks you through:

- Accessing the **CSE GitLab**
- Connecting to the **UNT network**
- Connecting to a **CSE cell machine**
- Generating and configuring **SSH keys**
- Cloning a Git repository and configuring Git
---

## 1️⃣ STEP ONE: Prepare the Environment

#### 🔹 Connect to the UNT Network

You **must** be connected to the UNT network.

If you are off campus, connect using the UNT VPN: Below is the **LINK** on how to set up UNT VPN 

👉 https://aits.unt.edu/support/palo_alto_vpn.html


#### 🔹 Sign in to CSE GitLab

Once connected to the UNT network, go to:

👉 https://csegitlab.engineering.unt.edu/users/sign_in

Sign in using your **UEID credentials**.


#### 🔹 Connect to a CSE Cell Machine

Follow the official connection instructions:

👉 https://engineering.unt.edu/cse/sites/default/files/cell_machine_connections.pdf

After connecting successfully, you should see a terminal prompt similar to:

```bash
mc1862@cell11-cse:~$

```
---

## 2️⃣  STEP TWO: Generate SSH Key for GitLab
#### 🔹 Generate SSH Key

Run the following command on the cell machine:
```bash
mc1862@cell11-cse:~$ ssh-keygen 
Generating public/private rsa key pair.
Enter file in which to save the key (/nfs/home/STUDENTS/mc1862/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /nfs/home/STUDENTS/mc1862/.ssh/id_rsa
Your public key has been saved in /nfs/home/STUDENTS/mc1862/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:EuoafEy2gDUtUGsbbjNlNlVL4QH0XtaLGlVEn4LB/54 mc1862@cell11-cse
The key's randomart image is:
+---[RSA 3072]----+
|...  .+o=o.o+    |
| . o . + o.= . . |
|  B * . + =.o o  |
| = O o o + ..o   |
|. B + . S . ..   |
| o O . . o    .  |
|  o =   .    . . |
|   +          E  |
|  .              |
+----[SHA256]-----+

```
Press Enter (5 times) to accept the default file location

Leave the passphrase empty unless instructed otherwise
#### 🔹 Display Public SSH Key
```bash
mc1862@cell11-cse:~$ cat .ssh/id_rsa.pub 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDQLxkRVVHdNnnllYKsh/Rw+ZGazqohIwtaeqUyz5Up1A4bcH0S9UjBav+eyo1yJceV/4IBcDNMv5/a/GAkJXV/5voBvzUKUew+6qLpyxwW3r9hyjfvz9xIQgk+BCD3F9btzwyPcMkPuqOQqkOpZyM1wEryAykbEKYd4hDn/bCnTkG8asTmS6zOEUl4PpmZKaOjki35Gd+2fj40/cslnzvAcz6SJX6+gDQCzmIKKJu5ktin0Qlbvb5CMrIQ1PCg1XSDul0UUfwTUGgNupel95JVNaW4VLQqxGF+jl7/9l6u08cwKCaXnCkelPS/KY/QdzP5wYOeJnJibN3d2FWQ1e2NtdikvPKKP7qAVj####################################################################################################################w0IbVo2R8bj3lY+x8LJ+qek= mc1862@cell11-cse
```
Copy the entire output ⚠️ {from: ssh-rsa to: -cse}.


#### 🔹 Add SSH Key to GitLab

<img width="2543" height="1299" alt="Screenshot 1_step2" src="https://github.com/user-attachments/assets/112fcf6d-1277-4d30-89d6-affc9c4a6323" />


➡️ 1 - Click your profile icon and Select Preferences

➡️ 2 - Click SSH Keys on the left

➡️ 3 - Paste your public key

➡️ 4 - Click Add key

---
## 3️⃣ STEP THREE: Create Project Directory

#### 🔹 Create a project directory under your home folder:
```bash
mc1862@cell11-cse:~$ mkdir demo && cd demo
mc1862@cell11-cse:~/demo$ 
```
---
#### 🔹 Set the Git Repository
```bash
mc1862@cell11-cse:~/demo$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint: 
hint:   git config --global init.defaultBranch <name>
hint: 
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint: 
hint:   git branch -m <name>
Initialized empty Git repository in /nfs/home/STUDENTS/mc1862/demo/.git/

```
#### 🔹 Replace project address with your actual repository path:
<img width="1041" height="744" alt="Screenshot 2_gitinit" src="https://github.com/user-attachments/assets/a8bc4c16-ef30-4efc-80ab-5320450404b8" />

```bash
mc1862@cell11-cse:~/demo$ git clone git@csegitlab.engineering.unt.edu:mc1862/demo.git
Cloning into 'demo'...
The authenticity of host 'csegitlab.engineering.unt.edu (129.120.151.4)' can't be established.
ED25519 key fingerprint is SHA256:6m7Muc4NAu2NUkcmMDXX0h9Vb2ZHHG58sH+A9Fj6qkI.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'csegitlab.engineering.unt.edu' (ED25519) to the list of known hosts.
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.

```
#### 🔹 Configure Git User Information

Configure your Git identity (required before committing):
```bash
mc1862@cell11-cse:~/demo$ git config --global user.name "Mav"
mc1862@cell11-cse:~/demo$ git config --global user.email maverickcheung@my.unt.edu
```
Verify:
```bash
mc1862@cell11-cse:~/demo$ git config --global --list 
user.name=Mav
user.email=maverickcheung@my.unt.edu
```
