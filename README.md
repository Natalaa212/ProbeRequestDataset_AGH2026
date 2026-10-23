# ProbeRequestDataset_AGH2026

A dataset of Wi-Fi Probe Request captures from **23 mobile devices**, containing **24,421 frames** across **115 PCAP files**.

## Dataset structure

Each directory (`A`–`W`) corresponds to the device with the matching ID in the table below. Each device directory contains five capture files: `1.pcap`, `2.pcap`, `3.pcap`, `4.pcap`, and `5.pcap`. File numbers distinguish captures within a device directory; they do not encode measurement conditions.

```text
ProbeRequestDataset_AGH2026/
├── README.md
├── A/
│   ├── 1.pcap
│   ├── 2.pcap
│   ├── 3.pcap
│   ├── 4.pcap
│   └── 5.pcap
├── B/
│   └── ...
├── ...
└── W/
    └── ...
```

## Devices

Manufacturer, model, and operating system versions are supplied measurement metadata. POCO and Redmi devices are listed under Xiaomi, with their brands retained in the model names. Total Frames is the sum of records in the five PCAP files for each device, verified directly against the captures.

| ID | Manufacturer | Model | Operating System | Total Frames |
|---|---|---|---|---:|
| A | Samsung | Galaxy A16 | Android 16 | 774 |
| B | Samsung | Galaxy A25 | Android 16 | 649 |
| C | Samsung | Galaxy A51 | Android 13 | 803 |
| D | Samsung | Galaxy A52 | Android 14 | 2013 |
| E | Samsung | Galaxy A57 | Android 16 | 1080 |
| F | Samsung | Galaxy S23 | Android 15 | 1762 |
| G | Samsung | Galaxy S25 Ultra | Android 16 | 2237 |
| H | Google | Pixel 10 Pro | Android 17 | 180 |
| I | HONOR | Magic8 Lite | Android 16 | 1098 |
| J | Motorola | edge 40 neo | Android 15 | 444 |
| K | realme | 12+ 5G | Android 16 | 1663 |
| L | Xiaomi | POCO X7 Pro | Android 16 | 805 |
| M | realme | 14 Pro+ 5G | Android 16 | 1580 |
| N | Xiaomi | Redmi Note 13 | Android 14 | 1841 |
| O | Samsung | Galaxy A54 | Android 16 | 3396 |
| P | Samsung | Galaxy M23 | Android 14 | 309 |
| Q | Xiaomi | POCO X3 | Android 11 | 682 |
| R | Apple | iPhone 14 Pro | iOS 26.6 | 237 |
| S | Apple | iPhone 16 | iOS 26.6 | 382 |
| T | Apple | iPhone 16 Pro | iOS 26.5 | 570 |
| U | Apple | iPhone 17 | iOS 26.6 | 209 |
| V | Samsung | Galaxy S21 | Android 15 | 1307 |
| W | Apple | iPhone 14 | iOS 27 | 400 |
| **Total** | | | | **24421** |

## Capture format and verification

All 115 files use the PCAP format with Radiotap headers. All 24,421 records are Wi-Fi Probe Request frames. Their source addresses are unicast addresses with the locally administered (U/L) bit set. This is consistent with possible MAC address randomization, but does not prove it. Counts refer to frames, not unique MAC addresses.

Directory labels provide the supplied device assignment; they do not independently establish that every frame originated from that device.

## Opening the captures

Open any `.pcap` file in Wireshark to inspect its frames. To display Wi-Fi Probe Requests, use the display filter:

```text
wlan.fc.type_subtype == 0x04
```
