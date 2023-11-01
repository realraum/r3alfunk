# Testing SDR++ Setup in R3 fpr shortwave RX

## Setup description:
* SDR++ with QDX (http://qrp-labs.com/qdx) used as a receiver at remote site
* Connection via VPN over LTE internet access at remote site (Ping ~ 30-50ms)
* Using rigsync and rigctld to keep local TRX and QDX RX in sync

## Random notes / things found during usage
* Signal delay is acceptable for phone even when band is busy
* Reception of QDX is very good
* Rigsync latency noticeable
* Rigsync can not handle difference between USB/LSB and USB-D/LSB-D on icom ic7300 -> need to disable rigsync when using digital modes
* Need to switch USB/LSB manually in SDR++
