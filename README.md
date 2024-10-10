# Tasmota-Rules
Timers and Rules for Tasmota

# E-Bike Battery Charge stop on float
Battery charges at 170W, when battery is getting full -> power is dropping over 1h -> so up to 100Wh are not charged if tasmota shut off at lower than 150W.
Remember to fully load battery one a month or ever 5 charges to make balancing possible. 

Inspiration from Github: 
https://github.com/arendst/Tasmota/discussions/17244

```
Rule1
   on Energy#Power<150 do RuleTimer1 100 endon 
   on Energy#Power>150 do RuleTimer1 0 endon
Rule2 
   on Rules#Timer=1 do Power OFF endon
Rule1 1
Rule1 5
Rule2 1
```


# Shut automatically off, after switch on
Switch is switched on to start a water pump. after x minutes, it should switch off by itself to stop water flow

```
SetOption26 1

PulseTime 60 = 6 Sec
PulseTime 100 for 10 Sec
```
>0 / OFF = disable use of PulseTime for Relay<x>

>1..111 = set PulseTime for Relay<x> in 0.1 second increments

>112..64900 = set PulseTime for Relay<x>, offset by 100, in 1 second increments. Add 100 to desired interval in seconds, e.g., PulseTime 113 = 13 seconds and PulseTime 460 = 6 minutes (i.e., 360 seconds)
