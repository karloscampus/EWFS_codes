# EWFS Codes
Reverse Engineering of 433MHz Codes for Warema EHFS Handsender 8K

Wondering, why there ist no documentation for the commands of the EWFS Handsender 8K (Atr.Nr.: 1002552). Frequency 433.92MHz.

Tried to scan an reverse the Manchester Encoding.

results als commited in aircontrol.conf.

you can test it with airControl (https://github.com/rfkd/aircontrol) installed on Rasbperry Pi and e.g. DEBO 433 RX/TX install on GPIO Pin 17 and 27.  

```
git clone https://github.com/karloscampus/EWFS_codes

cd EWFS

aircontrol -c ./aircontrol.conf -t warema_down
aircontrol -c ./aircontrol.conf -t warema_down2
aircontrol -c ./aircontrol.conf -t warema_down3
aircontrol -c ./aircontrol.conf -t warema_down4
aircontrol -c ./aircontrol.conf -t warema_down5
aircontrol -c ./aircontrol.conf -t warema_stop
aircontrol -c ./aircontrol.conf -t warema_stop2
aircontrol -c ./aircontrol.conf -t warema_stop3
aircontrol -c ./aircontrol.conf -t warema_stop4
aircontrol -c ./aircontrol.conf -t warema_stop5
aircontrol -c ./aircontrol.conf -t warema_up
aircontrol -c ./aircontrol.conf -t warema_up2
aircontrol -c ./aircontrol.conf -t warema_up3
aircontrol -c ./aircontrol.conf -t warema_up4
aircontrol -c ./aircontrol.conf -t warema_up5
```
# Background
Encoded with Manchester.

```
warema_up: 
{
airCommand = "S01110100111111" //command
"S000110101" // Device
"S001010100" // Device
"S";
};
```

where 
Sxx110100yyyzzz

x = some kind of crc (01 for up and down, 00 for stop)
y = channel (0-7), negated bits (111 for 0 and 000 for 7)
z = command (111 up, 110 down, 001 stop)


