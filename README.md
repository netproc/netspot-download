# NetSpot 6.1.0.830 Download for Windows — Wi-Fi Survey

NetSpot turns a floor plan into a coverage map. You import the plan, set its scale from two points of known distance, then walk the space and click once per measurement spot; each click records RSSI, SNR, noise, channel width and the access point in range, and the app interpolates a heatmap between the samples. Discovery mode is the faster half: it lists every nearby BSSID with security type, channel, band, maximum rate and a running signal history, which is usually enough to spot a channel that is oversubscribed or an AP that was left on defaults. Planning mode works from the plan alone, before anyone walks the site, and estimates coverage from wall materials. Projects export to CSV and PDF, and the free edition covers discovery plus a small survey while larger jobs need a licence.

<p align="center">
  <a href="https://cdn.netspotapp.com/download/Win/NetSpot.exe">
    <img src="https://img.shields.io/badge/DOWNLOAD-NetSpot_6.1.0.830-1B5E9B?style=for-the-badge&logo=windows&logoColor=white" alt="Download NetSpot">
  </a>
</p>

| | |
|---|---|
| **Version** | 6.1.0.830 |
| **Package** | `NetSpot.exe` — 36.4 MB |
| **Architecture** | x64 |
| **Platform** | Windows 10, Windows 11 |
| **License** | Freemium |

## Download

| Package | Size | Link |
|---|---|---|
| **NetSpot 6.1.0.830** | 36.4 MB | [Download](https://cdn.netspotapp.com/download/Win/NetSpot.exe) |

The link resolves to the distribution CDN for the current build, and the checksum file is published beside it so the download can be verified before installation.

## Works with

- Windows 11 (x64)
- Windows 10 1903 and newer
- Laptops with Intel, Qualcomm or MediaTek Wi-Fi cards
- 6 GHz surveys on a Wi-Fi 6E adapter with a current driver
- macOS 12 and newer — separate build, same project format

## SHA-256 checksum

```
63366227F29F626F0278E68586C79135533A0DAFBCAEF2732B510230E1127A89  NetSpot.exe
```

```powershell
Get-FileHash .\NetSpot.exe -Algorithm SHA256
```

Compare the full 64-character digest. A mismatch points to an interrupted transfer rather than a changed file, so retry once and stop if it repeats.

## Install

1. Run `NetSpot.exe`; the wizard installs in well under a minute and needs no reboot.
2. Choose a per-user or all-users install and confirm the target folder.
3. On first launch pick **Discover**, **Survey** or **Plan**, then select the wireless adapter — a laptop with both Wi-Fi and Ethernet shows only the Wi-Fi card here.
4. Windows asks for location access on first run — grant it, or the WLAN scan returns nothing, since the scan API is gated behind that permission.
5. For a scripted rollout the installer accepts `/VERYSILENT /NORESTART`; the first launch still needs a desktop session.

## What it does

- Passive and active scanning across 2.4, 5 and 6 GHz
- Heatmaps for signal level, SNR, interference, noise and throughput
- Floor plan import with per-point measurements and multi-floor projects
- Signal and channel history for every BSSID, with first and last seen
- Planning mode that estimates coverage from walls and materials
- Survey export to CSV and PDF

## Compatibility

NetSpot reads the wireless environment through the native Windows WLAN API, so it works with the card the laptop already has — no monitor-mode adapter and no packet capture driver. What the card reports is what the survey can show: an Intel AX-series or a recent Qualcomm module returns neighbour details and 6 GHz channels, while older 802.11n cards return a shorter list and no band information above 5 GHz. USB adapters work when their driver exposes the same API, which most NDIS drivers do.

Location Services must be on, under Settings → Privacy → Location. Windows gates WLAN scans behind that switch, and the failure looks like an empty network list rather than a permission error. Virtual machines are the other common dead end: a hypervisor without USB or PCIe passthrough presents no wireless adapter at all, so the survey modes stay greyed out while discovery simply finds nothing.

Windows 10 1903 and newer and Windows 11 are the supported desktop platforms. Band steering, DFS channels and 320 MHz widths are measured as the adapter sees them, so a survey done on older hardware will under-report what a client with a newer card can actually reach.

## Troubleshooting

**The network list is empty.** — Location Services is off, the Wi-Fi radio is disabled, or the selected adapter is a virtual one. Turn the radio on, re-enable location access, then reselect the card.

**Every survey point shows the same colour.** — The floor plan scale was never set, so the whole plan collapses to one distance. Re-calibrate with two points of known length and take at least a dozen samples per room.

**6 GHz networks are missing.** — The adapter is not 6E, the driver is old, or the region does not allow the channel. Check the card's capabilities before blaming the scan.

**A heatmap ignores a wall that clearly blocks signal.** — Wall material is a prediction input, not a measurement. Draw the wall and set its attenuation, or rely on measured points where accuracy matters.

**Active survey fails on a corporate SSID.** — Active mode associates with each network to measure throughput, which 802.1X or a captive portal will refuse. Use passive mode there.

**The project opens without its floor plan on another PC.** — The image path was absolute. Keep the plan beside the project file, or re-import it and re-place the points.

## Alternatives

- **Ekahau** — the professional survey suite, with a dedicated adapter and predictive design; priced for site surveys as a service.
- **Acrylic Wi-Fi** — scanner with a free tier and a paid edition that adds survey grids on Windows.
- **inSSIDer** — channel-graph analysis rather than coverage mapping; better for choosing a channel than for proving coverage.
- **TamoGraph Site Survey** — heatmaps and spectrum analysis with a similar workflow.
- **Hamina** — browser-based predictive planning, useful when the site cannot be walked yet.

## FAQ

**Is NetSpot free?** — Freemium. Discovery and a small survey work without a licence; larger projects, planning and exports need one.

**Does it need a special adapter?** — No. It uses the laptop's own Wi-Fi card. A 6E card is only needed for 6 GHz data.

**Can it measure without walking the site?** — Planning mode predicts coverage from the floor plan and wall materials. Measured heatmaps still need sample points.

**Does it run on Windows 11?** — Yes, on x64 builds; Windows 10 22H2 uses the same installer.

**Can it be installed silently?** — Yes, `/VERYSILENT /NORESTART` runs the installer unattended.

**Does it change any radio settings?** — No. It reads scan results and never reconfigures the adapter, the drivers or the access points.

## Disclaimer

Version data, the installer link and the SHA-256 digest are collected here for offline installation and archiving. Product names and trademarks belong to their respective owners. No affiliation or endorsement is implied.
