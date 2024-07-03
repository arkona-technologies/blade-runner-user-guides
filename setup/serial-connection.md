# Serial USB Terminal

In this short guide you will see how to:

- Connect a smartphone via serial connection to a blade
- Configure basic setups like IP addresses via smartphone

This guide is based on an android app called "Serial USB Terminal" and will provide some command examples.

## Get prerequisites

To get going, you'll need:

- The app:
  - Go to the google app store and download "[Serial USB Terminal](https://play.google.com/store/apps/details?id=de.kai_morich.serial_usb_terminal&hl=de&gl=US)". (This setup has been tested with version 1.53)
- A cable to connect your phone to the micro USB front port of the AT300


## Setup

1. Open Serial USB Terminal on your phone
2. Load the configuration file by clicking on the config button in the upper right corner (the button showing three dots - also known as the kabob menu) and then "configuration -> import" 

![Kabob menu (three dots)](serial-usb-app.png)

3. Connect your phone to the blade 

![Connect smartphone to AT300](smartphone-at300.svg)

4. In the app, go to "USB Devices" 

![Serial USB Terminal - Devices](serial-usb-app-devices.png)

5. Click on the serial device the app has found 

6. You should see a `connected to FTDI device` message and also a row of buttons:

![macro buttons](macro-buttons.svg)

7. Clicking on the "Login" button at the bottom, a message like this should appear 

```
[neighborhood-watch][AT300-59] p0@172.16.59.0 
p1@172.16.59.1 rear@172.16.59.2
root
Password:
AT300-59:/
root # [neighborhood-watch][AT300-59] p0@172.16.59.0 
p1@172.16.59.1 rear@172.16.59.2
```
8. The "Info-R" button will show you the current rear port address info 

9. With "Stat-R" you can change the rear mgmt IP address due to the configuration of the button (see config file) 

10. Reboot machine with "Reboot" button 


### Config file example

[Config example](./serial_usb_terminal_cfg.txt)