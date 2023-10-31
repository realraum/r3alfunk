# r3alfunk
Idea collection for realfunk

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
* 20m vertical Groundplane

### RX:
* Manually synchronized Websdr (https://websdr.iks.tugraz.at/kw)
  * Pro: Low QRM
  * Con: High delay (bad for digimodes that require low trx delay ("fast response"))

### Modes:
* SSB Voice (RX in websdr)
* FT-8 (RX locally + websdr possible)
* SSTV (RX in websdr)
* ARDOP (testing in progress, requires lower QRM + low RX delay, only on dummyload)

### Devices:
* ICOM IC-7300 (Gebi) -> Digimodes + SSB voice on HF
* Yaesu FT-857 (Jü) -> SSB-Voice + 2m/70cm FM/SSB
* QJE PS30SWIV (GNU/Fox) -> 30A 13.8V Power supply, allows 100W on HF + 50W on 2m at the same time

## Ideas
Ideas on improving/extending existing equipment + adding new equipment
### TX
* Add more elements to the vertical setup, as described by ernst -> multiband vertical -> 40m - 10m HAM-radio band coverage
* Try horizontal loop on 80m with 4:1 BalUn that can handle at least 100W continuos (old balun melted)
* Install Facilities for raising / lowering wires in the attic at the very top of the roof
* Install more coax to the roof

### RX
* Browser plugin for synchronizing local TRX with websdr frequency
  * Pro: Any websdr can be used, any local trx can be used (rigctld + hamlib handles abstraction)
  * Con: Always have to "chase" after websdr javascript code changes, no "full control" over the entire system on our part, does not solve the delay problem
* RF over fiber (RFoF):
  * Pro: "Exclusive" RX antenna, can be split using passive Fiber splitters ("Beam splitter"), low/no delay, RX can be local (TRX with R/T switch or separate SDR RX)
  * Con: requires exclusive dark fiber from R3 funkbude to RX-site (maybe in conjunction with TUGraz projects (?))
* SDR RX Site with IQ stream to realraum (gigabit? Funkfeuer?) + development of software solution that syncs local TRX (non web-technology based,  GNURadio (?))
  * Pro: Does not require exclusive cable/fiber, could have better latency than websdr, prior work has been done (https://github.com/ka9q/ka9q-radio)
  * Con: Probably requires a lot of work to become a user friendly solution
* https://github.com/jks-prv/kiwiclient
  * Pro: Does not require any new hardware (uses existing KiwiSDR), does not require browser, can be controlled via hamlib/rigctl (sync rigs: https://github.com/daveriesz/rigsync)
  * Con: Might still have noticeable delay, no waterfall
* SDR++ Server (https://github.com/AlexandreRouma/SDRPlusPlus):
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
* find out what Aronia is doing
