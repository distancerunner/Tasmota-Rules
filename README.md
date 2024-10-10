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
