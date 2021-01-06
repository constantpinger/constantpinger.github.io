---
layout: default
title: About
nav_order: 1
nav_exclude: false
canonical_url: https://www.google.com
search_exclude: false
---

# Raritan PX1 Command Line
The Raritan PDU that you can buy in 2021 are a robust piece of kit with a built in management module consisting of a modern web and SSH system. Older systems aren't so lucky. This post describes what you can do on the first generation PX command line. The following is based upon a model PX-5469 running firmware: 01.05.08

Raritan calls this the Command Line Protocol (CLP) interface and the manual states "enables data center administrators to perform some basic management tasks". They aren't joking when they say basic. Here is what they state:

*   Reset the Dominion PX device
*   Display the name, power state (on or off), and sensors associated with each outlet
*   Turn each outlet on or off 
*   Display the status of the sensors associated with each outlet

However, not even these are possible in reality. In particular you cannot tell the name you've configured to an outlet and so you'll need to know the number associated with the critical piece of infrastructure before you power cycle it.


## Basic Command Structure
Commands at the root level are ** cd help set show **. Ignore the help & cd ones one from the start as they don't do anything useful. In my experience if you can log onto the management you don't need to reset it. So that leaves show commands (check the outlet is correct) and set commands (power cycle the thing).


## Check the Outlet
You view info with the show command which works in a tree structure. Items under system1 are electrical. Items under the other branch named system2 are administrative. An example command for a known outlet is below:

```
clp:system1-> show /system1/outlet4
/system1/outlet4
 Properties:
  Name is OUTLET4
  powerState is 1 (on)

 Associations:
  CIM_AuthorizedTarget => /system2/authorizedpriv5
  CIM_SystemDevice => /system1
  CIM_AssociatedSensor => /system1/ncurrsensor7
  CIM_AssociatedSensor => /system1/nsensor14
  CIM_AssociatedSensor => /system1/ncurrsensor8
  CIM_AssociatedSensor => /system1/nsensor15
  CIM_AssociatedSensor => /system1/nsensor16
  CIM_AssociatedSensor => /system1/nsensor71

```

The actual name of the outlet as viewed in the web interface and SNMP query is that set by the admin. This interface fails to show that. So if you need to be sure about power cycling the right thing then you'll need to know the outlet number in advance. The only other clue might be from the current draw on the outlet (e.g. if zero this outlet doesn't have a powered on device attached).

The Associations are sensors for that outlet such as the current and voltage. The table below shows you what each does based on the above example (the order is the same for each outlet even though sensor IDs vary). Use the show command followed by the item below to find the value.



| show command         | WebUI label          | notes |
|:---------------------|:------------------|:------|
| /system1/ncurrsensor7 | RMS Current | actual amps drawn  |
| /system1/nsensor14 | power factor ratio |   |
| /system1/ncurrsensor8 | Maximum RMS Current |    |
| /system1/nsensor15 | Active Power |   |
| /system1/nsensor16 | Apparent Power |   |
| /system1/nsensor71 | Active Energy | total drawn power measured in watt-hour|


## Power Cycle an Outlet

There is no cycle command as such so to perform that task issue an off, and then an on command:

```
set /system1/outlet5 powerState=off
set /system1/outlet5 powerState=on
```



## Reset Management
```
reset /system1
```

## Notes
*   You can't use backspace so if you make a type you'll need to put some random characters in and press enter
*   [Link to a manual](https://www.manualslib.com/manual/933117/Raritan-Dominion-Px.html?page=188#manual)
*   Issuing the **/system2/log1** command will cause the management module to fail for two minutes (perhaps in my DC only?) with even ping not responding

