# NS2 Mobility Helper
### About
This is an update to the *Ns2MobilityHelper* class included in NS-3 Network Simulator to support 3D movement.

It implements the new statement:

```{r}
   $ns at $time $node setdest x2 y2 z2 speed
```

so that 3D destinations are allowed.

For reference, the statement originally specified in NS2 trace files are:
```{r}
   $node set X_ x1
   $node set Y_ y1
   $node set Z_ z1
   $ns at $time $node setdest x2 y2 speed
   $ns at $time $node set X_ x1
   $ns at $time $node set Y_ Y1
   $ns at $time $node set Z_ Z1
```

### Update Procedure

Simply copy the files *ns2-mobility-helper.h* and *ns2-mobility-helper.cc* into the folder:

 `./src/mobility/helper/ns2MobilityHelper/`

### Bug Fix

This update also fixes a bug (existing at least in ns-3.29), where statements of type `$ns at $time $node set ...` set the specified node's coordinate during parsing of the ns2 trace file, overriding the initial coordinate set with `$node set ...`, which could also lead to the node deviating from the expected movement pattern.
