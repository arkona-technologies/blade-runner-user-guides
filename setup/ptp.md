# Simple PTP setup

## Set PTP clock to FreeRun

- Go to the Blade//runner menu -> Quick Setup
- Click on "PTP FreeRun"

## Lock to PTP master

- Go to the Blade//runner menu -> Quick Setup
- Click on "PTP Client Wizard"
- Enter the domain
- Select the interfaces
- Select unicast/multicast mode
- Click "Save"
- Blade//runner will try to lock to a PTP master

## Lock to Analog Ref (coming with next release of 2.8)

- Go to the Blade//runner menu -> Quick Setup
- Click on "PTP Analog Ref"
- Blade//runner will try to use Analog Ref as its source for PTP clock

## Configure the blade as a PTP Master

- Go to the Blade//runner menu -> Quick Setup
- Click on "PTP Master Wizard"
- Set the domains and interfaces
- Click "Save"
- Blade//runner will try to setup the blade as a PTP master
  - if a MSC2 module and satellites are found, it will try to use its GPS data

## TL;DR video

- [Simple PTP setup via GUI](https://www.dropbox.com/scl/fi/9wobrfh7528p2m2wmblfi/ptp-setup.mp4?rlkey=7ji51t8l7smrd0mhdfzptgrf1&st=fytrhus8&dl=0)
