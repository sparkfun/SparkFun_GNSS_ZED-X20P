## Configuration Database

All configuration settings are stored in a database by the receiver.

The configuration database in the receiver's RAM holds the current configuration, which is used by the receiver at run-time. It is constructed on startup of the receiver from the configuration layers. The current configuration is called the RAM Layer. Any configuration in any layer is organized as Configuration Items, where each Configuration Item is referenced to by a unique Configuration Key ID and holds a single Configuration Value.



## Configuration Layers
The receiver has several configuration layers, some of the layers are read-only and others are modifiable. The layers are organized in terms of priority. Values in a high-priority layer replace values stored in a low-priority layers. At startup, the receiver reads all configuration layers and stacks up the items to create the current configuration, which is used by the receiver at run-time.

The following configuration layers are available (in order of priority, highest priority first):

1. **RAM**
:   This layer contains items stored in volatile RAM. This is the Current Configuration. The value of any item can be set by the user at run-time (see UBX protocol interface) and it is effective immediately.
1. **BBR**
:   This layer contains items stored in the battery-backed RAM. The contents in this layer are preserved as long as a battery backup supply is provided during off periods. The value of any item can be set by the user at run-time (see UBX protocol interface) and it becomes effective when the receiver is restarted.
1. **Flash**
:   This layer contains items stored permanently in the external flash memory. This layer is only available if there is a usable external flash memory. The value of any item can be set by the user at run-time (see UBX protocol interface) and it becomes effective when the receiver is restarted.
1. **Default**
:   This layer contains all items known to the running receiver software and their hard- coded default values. Data in this layer is not writable.


4.4.1 UBX protocol interface
The following UBX protocol messages are available to access the Configuration Database:
- `UBX-CFG-VALGET` to read configuration items from the database
- `UBX-CFG-VALSET` to set configuration items in the database
- `UBX-CFG-VALDEL` to delete configuration items from the database






4.7 Configuration reset behavior
The RAM layer is always rebuilt from the layers below when the chip's processor comes out from
reset. When using UBX-CFG-RST the processor goes through a reset cycle with these reset types
(resetMode field):
- `0x00` hardware reset (watchdog) immediately
- `0x01` controlled software reset
- `0x04` hardware reset (watchdog) after shutdown
See section Forcing a receiver reset in the integration manual.



### Configuration Items

| Group | Description |
| :---- | :---------- |
| `CFG-HW`           | Hardware configuration |
| `CFG-I2C`          | Configuration of the I2C interface |
| `CFG-I2CINPROT`    | Input protocol configuration of the I2C interface |
| `CFG-I2COUTPROT`   | Output protocol configuration of the I2C interface |
| `CFG-MSGOUT`       | Message output configuration |
| `CFG-NMEA`         | NMEA protocol configuration |
| `CFG-RATE`         | Navigation and measurement rate configuration |
| `CFG-SPI`          | Configuration of the SPI interface |
| `CFG-SPIINPROT`    | Input protocol configuration of the SPI interface |
| `CFG-SPIOUTPROT`   | Output protocol configuration of the SPI interface |
| `CFG-TP`           | Time pulse configuration |
| `CFG-UART1`        | Configuration of the UART1 interface |
| `CFG-UART1INPROT`  | Input protocol configuration of the UART1 interface |
| `CFG-UART1OUTPROT` | Output protocol configuration of the UART1 interface |







`CFG-NAVMASK-SV_MASK_GPS` - Satellite mask for the GPS system
`CFG-NAVMASK-SV_MASK_GAL` - Satellite mask for the Galileo system
`CFG-NAVMASK-SV_MASK_BDS` - Satellite mask for the BeiDou system
`CFG-NAVMASK-SV_MASK_QZSS` - Satellite mask for the QZSS system
`CFG-NAVMASK-SV_MASK_NAVIC` - Satellite mask for the NavIC system

CFG-HW-RF_LNA_MODE Sets the gain mode of the chip internal LNA for the L1 and L5 band independently of each other




