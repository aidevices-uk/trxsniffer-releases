# TRxSniffer

Windows console for IEEE 802.15.4 and ZigBee capture. The program listens on this PC only (`http://127.0.0.1:5080`).

This repository is the download. The current build is an **alpha**. The application source is not published here.

## Licence

The download does not include a licence. Capture will not start until you install one.

Email **info@aidevices.uk** with:

- the email address the licence should be issued to
- sniffer count: 1, 4, 8, 16, or unlimited
- whether you need Sub-GHz
- the term: a number of weeks, monthly, yearly, or unlimited

You receive a `TRX1` licence. In the console, open **Install licence**, paste that text, and save it. Then restart capture. Do not send a public or private key, and do not paste one into the console.

## Install

You need 64-bit Windows 10 or Windows 11.

1. Install [MongoDB Community Server](https://www.mongodb.com/try/download/community) and leave it running on this PC. Set its port to **37017** and bind it to `127.0.0.1`. That keeps TRxSniffer off a database you already run on the default port 27017. In `mongod.cfg`:

   ```yaml
   net:
     bindIp: 127.0.0.1
     port: 37017
   ```

   Restart the MongoDB service after saving that file. The console calls this packet storage and does not show the address.
2. Download [TRxSniffer 0.1.0 alpha for Windows](https://github.com/aidevices-uk/trxsniffer-releases/releases/download/v0.1.0-alpha/TRxSniffer-0.1.0-alpha-win-x64.zip).
3. Check the file if you want to: SHA256 `6af3e46ce3d2d3447af3cbbb4427a3c145d12179879af2130aca2130c7ff2997`.
4. Extract the zip and run `Start-TRxSniffer.cmd`.
5. The console opens at http://127.0.0.1:5080. Paste the licence, then press **Start**.

Windows may warn that the publisher is unknown. This build is not signed yet.

If packet storage shows **Unavailable**, MongoDB is not running.

## Sniffer

Flash the board with Texas Instruments Packet Sniffer 2, or use an nRF52840 running the nRF Sniffer for 802.15.4, or a Silicon Labs WSTK. Use the application UART, not an auxiliary port. Close any other program that has the COM port open, including SmartRF Sniffer Agent.

Add the port and channel on the Configure page, then start capture. One sniffer per channel is the default.

Wireshark shows **Bad FCS** on the default PCAP until IEEE 802.15.4 preferences use **TI CC24xx metadata**. That trailer is the signal strength, not a broken frame.
