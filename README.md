All power levels were recorded using the Energy page of the Info Center in KDE Plasma. I don’t know how accurate this tool is. Each measurement was taken by performing the activity and checking the energy menu periodically. The ranges represent the highest and lowest values that I observed. My brightness and volume were set to 50%, and my keyboard backlight was completely off.

### My Specs
- Framework 13 AMD AI 9 HX 370
- 128 GB Crucial DDR5-5600
- 2 TB Samsung 970 EVO Plus

### Using `power-profiles-daemon` power saving profile:
- **Idle**: 5.85W – 6.5W
- **LibreOffice Writer**: 8.5W – 9.5W
- **YouTube Playback**: 14.5W – 15.5W

### Using `tlp.service` battery profile:
- **Idle**: 5.4W – 5.8W
- **LibreOffice Writer**: 7W – 8W
- **YouTube Playback**: 12.2W – 13W

---

### Setup Instructions

1. **Install TLP:**
    ```bash
    sudo dnf install -y tlp
    ```

2. **Download `tlp.conf` and place it in `/etc/`:**
    ```
    sudo curl -o /etc/tlp.conf https://raw.githubusercontent.com/connor-petri/fw13-tlp-config/refs/heads/main/tlp.conf
    ```
    
3. **Disable and mask `power-profiles-daemon`:**
    ```bash
    sudo systemctl stop power-profiles-daemon.service && sudo systemctl mask power-profiles-daemon.service
    ```

4. **Enable and start TLP:**
    ```bash
    sudo systemctl enable --now tlp && sudo tlp start
    ```

---

When in auto mode, **TLP** will switch between battery and AC modes automatically.  
To force the use of a specific profile, use:

```bash
sudo tlp bat
sudo tlp ac
```
