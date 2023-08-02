# MaaXBoard-RT_cdc_vcom_freertos_cm7
 MaaXBoard-RT VCP UART example

## USB VCP UART demo from SDK
Project is example from EVKMIMXRT1170 SDK.
After patching files for MaaXBoard-RT (e.g. board.h, cdc.c and flash loader),
it was compile free and also WORKING!

## Extensions done
It uses FreeRTOS: But the App Task polls for VCP UART received character(s).
I have added to use FreeRTOS Queue Event to trigger App Task (now in blocking mode, waiting yo release the receiver App Task from USB stack).
USB stack sends event to release the App Task waiting for something received
(not polling anymore in full speed).

## VCP UART on USB-C device
This demonstrates, that the USB-C can be used as USB Device, the CDC (VCP UART)
class is instantiated and works.
Now, you can use USB-C only (needed for power), it provides also a VCP UART.

The LPUART, used on debugger (or via external UART-to-USB dongle), is not needed:
the board runs with a UART and just with USB-C as connection.

BTW: The original Debug UART (LPUART), is not working (in parallel).
It might be possible to enable this one again and as well (e.g. for debug purposes, as backdoor...).

## How to use?
Install all for the MaaXBoard-RT as documented by AVNET, find in:
[MaaXBoard+RT+User+Guide.pdf](https://www.avnet.com/wps/wcm/connect/onesite/15a1365e-b32e-488a-b355-e4c795934926/MaaXBoard+RT+User+Guide+%28v1.0%29.pdf?MOD=AJPERES&CACHEID=ROOTWORKSPACE.Z18_NA5A1I41L0ICD0ABNDMDDG0000-15a1365e-b32e-488a-b355-e4c795934926-nM9ynBT)

### Remark:
The "board.h" file has to be the latest version (find it in the project here).
The installation of the Flash Loader (and file) is slightly different:
I think, you have to copy also file into a workspace sub-folder (see the error message on debug start/flashing the board).

