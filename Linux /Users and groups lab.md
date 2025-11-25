# Managing Users and Groups in Linux

This lab shows how i can create users, manage groups, modify user and group settings, and simulate user logins in a Linux environment.

---

## The Scenario 

i was tasked with setting up user accounts for an organization. The details of users, their roles, and the default password are provided.

### The users i had to Create

#insert pic of the table!!!

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
```
#Enter the last image of the lab
---
