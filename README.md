<h1>Metasploitable 2 SMTP Hacking</h1>

<h2>Description</h2>

The project consists of using the information from the [enumeration project](https://github.com/ntieu4328/Metasploit-2-Enumeration) to exploit the Metasploitable 2 system. In this project, I will specifically exploit the SMTP portion of the Metasploitable 2 system. This is to gain user information from the SMTP server. SMTP stands for simple mail transfer prtocol which is used to send and receive mail messages.

<h2>Walk-through:</h2>

From the enumeration that was done, I can see that poty 25 is open:

![nmap smtp](https://github.com/ntieu4328/Metasploitable-2-SMTP-Hacking/assets/156137990/c3c99b2e-a1fa-4309-aa66-d7bfe849cc41)

This port is the default port the SMTP protocol.

Start Metasploit:

```bash
msfconsole
```

Search for the SMTP scanner

```bash
grep scanner search smtp
```

![smtp scans](https://github.com/ntieu4328/Metasploitable-2-SMTP-Hacking/assets/156137990/53909d41-87fc-4504-b120-939ef6006fea)

This shows the different SMTP scans that can be done.
  - smtp_version: Used to see what SMTP version is being run to see if it's out of date
  - smtp_relay: Used to see if it's a SMTP relay server
  - smtp_enum: Used to find user information

For this project I will use the smtp_enum scanner:

```bash
use 25
```

See what options need to be configured:

```bash
show options
```

![smtp_enum options](https://github.com/ntieu4328/Metasploitable-2-SMTP-Hacking/assets/156137990/8c7a46cf-446d-4dd0-822d-ffc603326653)

The RHOSTS option needs to be configured to the Metasploitable 2 IP:

```bash
set rhosts 10.0.2.4
```

Start the scan:

```bash
run
```

The scan verifies if a user account matches the user list that is used for he scan. The user list being used is unix_users.txt

<b>The scan will take a while</b>
