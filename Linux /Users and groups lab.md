# Managing Users and Groups in Linux

This lab shows how i can create users, manage groups, modify user and group settings, and simulate user logins in a Linux environment.

---

## The Task

I was tasked with setting up user accounts for an organization. The details of users, their roles, and the default password are provided.
<img width="1107" height="467" alt="Screenshot 2025-11-24 223748" src="https://github.com/user-attachments/assets/1211664a-d728-4af6-a251-5d0b7a27d05e" />

### The users i had to Create
<img width="1256" height="537" alt="Screenshot 2025-11-25 031834" src="https://github.com/user-attachments/assets/49b6b309-fdfe-4a4b-a6f6-bd0a856e72eb" />





The default password for all users was: `P@ssword1234!`

---

## The groups i had to Create

I created the following groups to represent departments and roles:

- sales
- hr
- finance
- personnel
- ceo
- shipping
- managers

---

## My tasks

### Check Existing Users:

To list the current users on the system i checked the `/etc/passwd` file:

```bash
cut -d: -f1 /etc/passwd
```

To filter only actual human (non-system) users by checking for UID >= 1000:

```bash
awk -F: '$3>=1000{print $1}' /etc/passwd
```

### To Create Groups

```bash
sudo groupadd sales
sudo groupadd hr
sudo groupadd finance
sudo groupadd personnel
sudo groupadd ceo
sudo groupadd shipping
sudo groupadd managers
```

---

### To Create Users and Set Passwords

Use the following pattern to create users:

```bash
sudo useradd -m -s /bin/bash arosalez
echo "P@ssword1234!" | sudo passwd --stdin arosalez
```

> 📝 For systems without `--stdin`, use:
```bash
echo "arosalez:P@ssword1234!" | sudo chpasswd
```

Repeat for each user using their respective User ID.

<img width="1920" height="898" alt="users groups3" src="https://github.com/user-attachments/assets/2409bc0c-ac01-4885-8ad7-1a6eaa6fe125" />

---

### Adding Users to Groups

I used the following command format:

```bash
sudo usermod -aG sales,managers arosalez
sudo usermod -aG shipping eowusu
sudo usermod -aG shipping jdoe
sudo usermod -aG hr,managers ljuan
sudo usermod -aG finance,managers mmajor
sudo usermod -aG ceo mjackson
sudo usermod -aG sales nwolf
sudo usermod -aG shipping psantos
sudo usermod -aG hr smartinez
sudo usermod -aG finance ssarkar
```

---

### Verifying Group Membership

The command i used
```bash
groups arosalez
groups ljuan
```

---

### To Modify User Info

Change user's shell or additional settings:

```bash
sudo usermod -s /bin/zsh jdoe
sudo usermod -c "Finance Manager" mmajor
```

---

### How i Simulated User Login

I used `su` to simulate login as a created user:

```bash
su - arosalez
whoami
exit

<img width="1920" height="922" alt="users groups4" src="https://github.com/user-attachments/assets/2bc52bf5-78ee-4b4c-b4a6-c3b6371b0066" />

```

---
