!!! warning "HPG v2.02"
    The binary strings for the UBX configuration of the GPS L5 signal, displayed below, are only valid with the latest **HPG 2.02 firmware** on the ZED-X20P.



## Health Status Configuration
The ZED-X20P supports GPS `L5` signals. Broadcasting of Civil Navigation (CNAV) messages on the `L5` signal began in April 2014. At the time of writing, the GPS `L5` signals remain pre-operational and they are set unhealthy until sufficient monitoring capability is established. To evaluate GPS `L5` signals before they become fully operational, the receiver can be configured to ignore the GPS `L5` health status by overriding it with the respective GPS `L1 C/A` signal status.

- Do not use unhealthy, pre-operational GPS `L5` signals for safety-of-life or other critical purposes. This is an operational issue concerning the satellites/space segment; not a limitation or specific configuration of u-blox products.
- Users who choose to ignore the GPS `L5` signal health status in their production system do so at their own risk and must be fully aware of the implications. The system should also include a mechanism to revert to the mode where the `L5` signal health status is respected.


## Enable GPS `L5` Signal
The receiver does not use unhealthy signals for navigation by default. To ignore the GPS `L5` signal health status and override it with the respective GPS `L1` signal health status, the following UBX binary strings can be used. To confirm that the above UBX messages are sent successfully to the receiver, check that a `UBX-ACK-ACK` message is received afterwards. The configuration can be stored in RAM, BBR (battery-backed RAM), and/or flash layers.

- Writing to RAM ensures the UBX messages are taken into use immediately.
- Writing to BBR allows the UBX message to be carried out at next power-on if battery backup is maintained.
- Writing to flash ensures the UBX message is taken into use at every startup until the firmware is replaced in flash.


<figure markdown>
<!-- { style="padding: 0 3em 0 1.1764705882em;" } -->
<table markdown>
<tr>
<th>Configuration layer</th>
<th>Configuration string</th>
</tr>
<tr markdown>
<td style="vertical-align: middle;">RAM</td>
<td style="padding-top: 0; padding-bottom: 0;" markdown>
``` { .hex .no-select }
B5 62 06 8A 09 00 01 01 00 00 01 00 32 10 01 DF F6
```
</td>
</tr>
<tr markdown>
<td style="vertical-align: middle;">BBR</td>
<td style="padding-top: 0; padding-bottom: 0;" markdown>
``` { .hex .no-select }
B5 62 06 8A 09 00 01 02 00 00 01 00 32 10 01 E0 FE
```
</td>
</tr>
<tr markdown>
<td style="vertical-align: middle;">FLASH</td>
<td style="padding-top: 0; padding-bottom: 0;" markdown>
``` { .hex .no-select }
B5 62 06 8A 09 00 01 04 00 00 01 00 32 10 01 E2 0E
```
</td>
</tr>
</table>
<figcaption markdown>Table 1: UBX binary string to override GPS `L5` signal health status with GPS L1 health status</figcaption>
</figure>


<!-- 
| Configuration layer | Configuration string |
| :---- | :--------------------------------------------------: |
| RAM   | `B5 62 06 8A 09 00 01 01 00 00 01 00 32 10 01 DF F6` |
| BBR   | `B5 62 06 8A 09 00 01 02 00 00 01 00 32 10 01 E0 FE` |
| FLASH | `B5 62 06 8A 09 00 01 04 00 00 01 00 32 10 01 E2 0E` |
-->



## Disable GPS `L5` Signal
To revert back to the default configuration, send the configuration string given in Table 2. The device returns the `UBX-ACK-ACK` message if the configuration is sent successfully.


<figure markdown>
<!-- { style="padding: 0 3em 0 1.1764705882em;" } -->
<table markdown>
<tr>
<th>Configuration layer</th>
<th>Configuration string</th>
</tr>
<tr markdown>
<td style="vertical-align: middle;">RAM</td>
<td style="padding-top: 0; padding-bottom: 0;" markdown>
``` { .hex .no-select }
B5 62 06 8A 09 00 01 01 00 00 01 00 32 10 00 DE F5
```
</td>
</tr>
<tr markdown>
<td style="vertical-align: middle;">BBR</td>
<td style="padding-top: 0; padding-bottom: 0;" markdown>
``` { .hex .no-select }
B5 62 06 8A 09 00 01 02 00 00 01 00 32 10 00 DF FD
```
</td>
</tr>
<tr markdown>
<td style="vertical-align: middle;">FLASH</td>
<td style="padding-top: 0; padding-bottom: 0;" markdown>
``` { .hex .no-select }
B5 62 06 8A 09 00 01 04 00 00 01 00 32 10 00 E1 0D
```
</td>
</tr>
</table>
<figcaption markdown>Table 2: UBX binary strings to revert the GPS `L5` signal health status monitoring to default</figcaption>
</figure>


<!-- 
| Configuration layer | Configuration string |
| :---- | :--------------------------------------------------: |
| RAM   | `B5 62 06 8A 09 00 01 01 00 00 01 00 32 10 00 DE F5` |
| BBR   | `B5 62 06 8A 09 00 01 02 00 00 01 00 32 10 00 DF FD` |
| FLASH | `B5 62 06 8A 09 00 01 04 00 00 01 00 32 10 00 E1 0D` |
-->
