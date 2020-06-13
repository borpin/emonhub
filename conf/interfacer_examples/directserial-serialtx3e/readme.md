# Direct Serial emonTx V3 / emonTH

Used for direct serial connection to the emonTX either via the emoneESP or to an Rpi.

by @owenduffy - Updated by @borpin June 2020

Interfacer for serial output from emonTx V3 (firmware V2.4 and above) Ds or CM.

emonTx firmware V2.4+ outputs serial CSV string pairs compatiable with emonESP:

`name:value,name:value`

e.g.
`ct1:100,ct2:300` ....

or CM data `MSG:59795,Vrms:245.85,P1:84,E1:9999,T1:22.75,pulse:1`

Default baudrate is `9600`

## Config example

Add the following to `emonhub.conf` in the `[interfacers]` section:

```text
[interfacers]
### This interfacer manages the data from the EmonTx3 Direct serial connection
[[SerialTx3e]]
     Type = EmonHubTx3eInterfacer
     [[[init_settings]]]
          # Un-comment line below if using RS485 adapter
          #com_port = /dev/ttyRS485-0
          # default com port if using USB to UART adapter
          com_port= /dev/ttyUSB0
          # com_port for direct connection to emonTX from RPi - @ 115200
          #com_port= /dev/ttyAMA0
          com_baud = 115200
     [[[runtimesettings]]]
          pubchannels = ToEmonCMS,
          #nodeoffset = 1           # Default NodeID is 0. Nodeoffset will be used as the NodeID
          #nodename = Serial_PiZ    # Optional - set NodeName
```

See [blog post](http://owenduffy.net/blog/?p=9942) by @owenduffy detailing serial connection an emonTx V3 (running stock V2.4+ FW) with RS485 adapter.

[Community Post](https://community.openenergymonitor.org/t/emontx-to-rpi-direct-serial-connection/13114/38) - connecting an RPi directly to an emonTX 3.4.
