# Ethernet Frame - [Challenge Link](https://www.root-me.org/en/Challenges/Network/ETHERNET-frame)

## 🧠 Summary
A raw Ethernet frame captured in hexadecimal contains an HTTP request. The goal is to extract the user credentials embedded in an HTTP Basic Authorization header.

**Theory (security):**
- Ethernet frames consist of a destination MAC, source MAC, EtherType/length, payload, and FCS. When captured and converted to bytes, the payload can include higher‑layer protocols (IP, TCP, HTTP).
- HTTP Basic Authentication encodes a username:password pair using Base64 and includes it in the `Authorization: Basic` header. Base64 is not encryption, merely encoding; anyone who can read the traffic (e.g. with a packet capture or raw frame log) can decode the credentials trivially.
- Basic auth should only ever be used over encrypted channels such as HTTPS. Insecure use exposes credentials to on‑path attackers. Even over HTTPS, it offers weak security compared to token‑based or more modern authentication schemes.

## 🧰 Tools Used
- cyberchef
- wget

## 💣 Exploitation / Solution
Step-by-step:

1. I downloaded the challenge file (`ch12.txt`) and ran `file ch12.txt` to see what I was dealing with; the output confirmed it was plain ASCII text.
2. Opening the file in an editor showed a long string of hexadecimal characters – it looked exactly like the raw packet bytes you’d get from Wireshark when viewing an Ethernet frame.
3. I copied the hex string into CyberChef and used the **From Hex** recipe. The decoded output was an HTTP request, which immediately told me where to look next.

   ![cyberchef-hex](cyberchef-hex.png)
4. Scanning the HTTP headers revealed an `Authorization: Basic` line. The challenge PDF about HTTP basic auth reminded me that the string following `Basic` is just Base64-encoded credentials.
5. I pasted `Y29uZmk6ZGVudGlhbA==` into CyberChef again, this time using **From Base64**, and the cleartext `password` appeared.

   ![cyberchef-base64](cyberchef-base64.png)

Conclusion: by treating the file as a hex dump of an Ethernet frame and decoding step by step, I recovered the HTTP Basic auth credentials. Since Base64 is easily reversible, anyone capturing the unencrypted frame would obtain the username and password, highlighting the weak security of HTTP Basic authentication without encryption.

## 🏁 Flag / Result
flag hash:
`bd24a4c4fc588be5955abf27d5344c2e3b60de74a38732190f3c3d401ca32c99`

## ✏️ Notes
- [Link to RFC-948](https://repository.root-me.org/RFC/EN%20-%20rfc1042.txt?_gl=1*1wd6kp4*_ga*NjYzOTI5NjYwLjE3NzIzMDYxNTU.*_ga_SRYSKX09J7*czE3NzIzMTM3MDYkbzMkZzEkdDE3NzIzMTUzOTAkajYwJGwwJGgw)