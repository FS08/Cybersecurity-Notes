# Ethernet Frame - [Challenge Link](https://www.root-me.org/en/Challenges/Network/ETHERNET-frame)

## 🧠 Summary
You have been asked by Cat Corporation’s SOC team to retrieve a user’s password linked to a suspicious Kerberos connection.

Flag format : RM{userPrincipalName:password}

* The userPrincipalName must be written in lowercase.

sha256sum: `0770efe5374637534fe55fdf51a3b7a1d5c58a1d6027d7143ce0a491ffd66405`

**Theory (security):**
- 

## 🧰 Tools Used
- cyberchef
- wget

## 💣 Exploitation / Solution
Step-by-step:

- download the challenge with wget 
- opened the .pcap file
- went to hashcat 

Conclusion: by treating the file as a hex dump of an Ethernet frame and decoding step by step, I recovered the HTTP Basic auth credentials. Since Base64 is easily reversible, anyone capturing the unencrypted frame would obtain the username and password, highlighting the weak security of HTTP Basic authentication without encryption.

## 🏁 Flag / Result
flag hash:
``
RM{william.dupond:}
cname = william.dupond


## ✏️ Notes
- [Link to hackndo Kerberos](https://beta.hackndo.com/kerberos/)
- [Link to Kerberos Brute-Force video](https://www.youtube.com/watch?v=VLA7x81i5Pw)