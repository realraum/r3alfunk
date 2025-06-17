# r3alfunk
Idea + Status collection for realfunk

## Goal
Make Realraum Funkraum useable for operation:
 * Be able to transmit on the bands:
   * At least: 40m to 10m + 2m + 70cm
   * Bonus: 80m + 6m + QO-100 uplink (13cm)
 * Be able to receive with lowest attainable QRM on the band:
   * At least: 40m to 10m + 2m + 70cm
   * Bonus: 80m + 6m + QO-100 downlink (3cm)
 * Be able to transmit and receive digital modes, example: SSTV, HamDRM, ARDOP (connect to Mailboxes), FT-8
 * Be able to transmit and receive SSB voice mode (HF, 2m ssb would be a bonus)

## Current State
Useable and tested frequencies/modes/facilities/devices
### TX:
* 40m, 30m, 20m, 15m, 12m, 10m vertical Groundplane
* 80m, (40m, 20m, 15m, 10m) horizontal loop (full-size for 80m)

### RX:
* __[DEPRECATED]:__ Manually synchronized Websdr (https://websdr.iks.tugraz.at/kw)
  * Pro: Low QRM
  * Con: High delay (bad for digimodes that require low trx delay ("fast response"))
* __[TESTING]:__ SDR++ with modified version of [rigsync](https://github.com/GNUFox/rigsync) and rigctld (see https://github.com/realraum/r3alfunk/blob/main/SDRpp_experience_test.md)

### Modes:
* __[SUCCESSFUL QSOs]__ SSB Voice (RX in websdr + with SDR++)
* __[SUCCESSFUL QSOs]__ FT-8 (RX locally + websdr possible)
* __[SUCCESSFUL QSOs]__ SSTV (RX in websdr + with SDR++)
* __[TESTING]__ HAMDRM (RX with SDR++ or websdr for verifying own signal)
* __[SUCCESSFUL QSOs]__ ARDOP + pat-winlink (RX with SDR++, sent multiple emails using 80m an a winlink node in austria)

### Devices:
* ICOM IC-7300 (Gebi) -> Digimodes + SSB voice on HF
* Yaesu FT-857 (Jü) -> SSB-Voice + 2m/70cm FM/SSB
* HIGHTECH (former "C-Netz" cellular network PSU) (R3) -> 60A (?) 13.8V Power supply, allows >100W on HF + 50W on 2m at the same time

## Ideas
Ideas on improving/extending existing equipment + adding new equipment
### TX
* __[DONE]__ Add more elements to the vertical setup, as described by ernst -> multiband vertical -> 40m - 10m HAM-radio band coverage
* __[CHANGED]__ Try horizontal loop on 80m with 4:1 BalUn that can handle at least 100W continuos (old balun melted)  
  --> using no balun and only air wound RF-choke works with IC-7300 Tuner on 80m
* __[DONE]__ Install Facilities for raising / lowering wires in the attic at the very top of the roof
* Install more coax to the roof

### RX
* __[ABANDONED]__ Browser plugin for synchronizing local TRX with websdr frequency
  * Pro: Any websdr can be used, any local trx can be used (rigctld + hamlib handles abstraction)
  * Con: Always have to "chase" after websdr javascript code changes, no "full control" over the entire system on our part, does not solve the delay problem
* __[INFO GATHERING]__ RF over fiber (RFoF):
  * Pro: "Exclusive" RX antenna, can be split using passive Fiber splitters ("Beam splitter"), low/no delay, RX can be local (TRX with R/T switch or separate SDR RX)
  * Con: requires exclusive dark fiber from R3 funkbude to RX-site (maybe in conjunction with TUGraz projects (?))
* SDR RX Site with IQ stream to realraum (gigabit? Funkfeuer?) + development of software solution that syncs local TRX (non web-technology based,  GNURadio (?))
  * Pro: Does not require exclusive cable/fiber, could have better latency than websdr, prior work has been done (https://github.com/ka9q/ka9q-radio)
  * Con: Probably requires a lot of work to become a user friendly solution
* __[ABANDONED]__ https://github.com/jks-prv/kiwiclient
  * Pro: Does not require any new hardware (uses existing KiwiSDR), does not require browser, can be controlled via hamlib/rigctl (sync rigs: https://github.com/daveriesz/rigsync)
  * Con: Might still have noticeable delay, no waterfall
* __[TESTING]__  SDR++ Server (https://github.com/AlexandreRouma/SDRPlusPlus):
  * Pro: Supports multiple receivers, looks feature laden, server + client software made for each other
  * Con: Not tested yet, no known 

## Unsorted Ideas / Brainstorming:
* QO-100 TRX: Transmit on 2.4 GHz with high power in shack to compensate for coax loss, keep roof instalation minimal (RX dish + LNB + TX antenna, No other active componenets)
* More power (400W 800W ???)
* Patch panel for SO239 / PL259 + N type connectors + Patch cords
* Data synchronization between PCs (R3 NAS?) + "online" logbook
* "More screens"
* Use https://luarvique.github.io/ppa/ on a QRM-free location over 0xff or dedicated WLAN (with low delay)
* work on https://github.com/ka9q/ka9q-radio as backend for SDR++ or other useful GUI
* redesign WebSDR/SDR buffer to
  * support more simultaneous users
  * allow receiving/downloading/schedule recording raw I/Q for a particular slice of spectrum
  * implement https://github.com/argilo/SigMF for metadata
  * allow integration of multiple receiver locations
* replace OpenWebRX with something more user friendly, in particular on mobile
* find suitable protocols for control and data plane
* look at what Aaronia is doing https://aaronia.com/de/shop/spectrum-analyzer/real-time/compact-usb/spectran-v6-x/spectran-v6-rsa-2000x
* consider advanced signal processing to get rid of noise, distortion, etc, inspired by tools like this: https://www.steinberg.net/de/spectralayers/
* world clock with grayline, DIY project, similar to https://www.wimo.com/de/geochron-atlas
* LNB Mods https://baltic-lab.com/2023/07/lnb-modification-for-10-ghz-qo-100-satellite-reception/
* QO-100 Groundstation Ideas https://github.com/realraum/r3alfunk/blob/main/QO100%20f%C3%BCr%20BG15.pdf
