# Definitions:
## SDR RX w/ demod = "SDR RX":
* Remote receiver
* Receiver connected to a pc for receiving and demodulating -> SDR
* Audio is sent via network to station for further processing / listening

## SDR RX w/o demod = "SDR RX IQ"
* Remote receiver
* only selectes band limited part of HF spectrum
* Sends I/Q over network to station
* Frequency selection and demodulation happens in station (software on pc)
* Could be converted back to HF in station

## RFoF
* Remote antenna + RFoF converter
* entire HF spectrum upconverted to CATV adaptor frequency range (~ 50-600 MHz)
* No sampling / band limiting at RX site
* RX in station with SDR or downconverter + normal RX

# Requirements
## SDR RX
* Finding and optimizing latency problems (buffer)
* Good Network connection (Wifi direct link or over 0xFF)
* __PLEASE ADD MORE__

## SDR RX IQ
* Same as "SDR RX"
* __PLEASE ADD MORE__

## RFoF
* Dark fiber to station
* upconverter at RX site
* possibly downconverter at station for use with normal RX + RX/TX Switch to protect RFoF Receiver
* SDR at station for waterfall view

# Comparing RFoF to remote SDR RX
Comparison on requirements and possibilities using RFoF or a remote SDR receiver.


- Fiber:
    - RX site may have slightly higher than ideal QRM (Lustbühel? Inffeldgasse roof?)
    - low latency and direct spectrum access is worth not having ideal RX conditions

- Network / remote SDR RX
    - RX site should have lowest possible QRM, network is much easire available than dark fiber
    - Latency should be very low (optimizing software is necessary)
    - Network connection should be exclusive or at least better than LTE (direct WiFi link? 0xFF?)
