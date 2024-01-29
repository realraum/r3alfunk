# Testing SDR++ Setup in R3 fpr shortwave RX

## Setup description:
* SDR++ with QDX (http://qrp-labs.com/qdx) used as a receiver at remote site
* Connection via VPN over LTE internet access at remote site (Ping ~ 30-50ms)
* Using rigsync and rigctld to keep local TRX and QDX RX in sync

## Usage Instructions
* start up rigctld in a terminal with correct parameters
* start up modified version of rigsync (https://github.com/GNUFox/rigsync)
* Start SDR++:
  * Connect to server (address is remembered by SDR++)
  * Press play button
  * __Keep demod frequency at 0__ (QDX demod freq. is controlled by CAT and it uses audio (L/R) for I/Q signal, demod freq. is not passed to SDR++)
  * Manually select USB / LSB (not synced between SDR++ and rig)
  * If there's no audio check Audio settings in OS + plugs/cables + speakers (enabled?)
* Now control operating frequency from the rig dial. 

## Random notes / things found during usage
* Signal delay is acceptable for phone even when band is busy
* Reception of QDX is very good
* Rigsync latency noticeable
* __[DONE]__ Rigsync can not handle difference between USB/LSB and USB-D/LSB-D on icom ic7300 -> need to disable rigsync when using digital modes
* Need to switch USB/LSB manually in SDR++
