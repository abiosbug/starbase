## Fuel and Propellant consumption

#### Info
Fuel and Propellant are consumables so calculating how fast you're draining them is pretty useful.
Propellant has 2 global variables that hold the total of all Propellant: `:GasNetworkStoredResource` and `:GasNetworkMaxResource`
Fuel on the otherhand has to be summed up for each Fuel Chamber to get the total value. In YOLOL you can use the following trick to sum up more values than the line length:

```
F=:Fuel1+:Fuel2+ ... 
F+=:Fuel10+:Fuel11+ ...
```


#### Rod/Propellant Time V3
_Existing script from Davemane42_

Adjustments:
Generator Fuel Chamber
   FuelChamberFuel -> `"RodFuel"` 

Propellant tank support
   GasNetworkStoredResource -> `"Propellant"`

Text Panel 24x24
    PanelValue -> `"TimeLeft"`
   `"\n---Rods---\nINF\n100 %\n---Prop---\nINF\n100 %\n"`

YOLOL:
```
n="\n" a="INF" b=" %" z="---" c=1000 m=60 h=3600 MR=300000 MP=40000000
d=e e=f f=g g=:RodFuel RD=((g-f)+(f-e)+(e-d))/3 RP=n+(g/MR)*100+b+n
RT=g/-RD RH=(RT/h)/c*c RM=((RT-RH*h)/m)/c*c RTL=RH+"h "+RM+"m "
i=l j=l k=l l=:Propellant PD=((l-k)+(k-j)+(j-i))/3 PP=n+(l/MP)*100+b+n
PT=l/-PD PH=(PT/h)/c*c PM=((PT-PH*h)/m)/c*c PTL=PH+"h "+PM+"m "
:TimeLeft=n+z+"Rods"+z+n+RTL+RP+z+"Prop"+z+n+PTL+PP RTL=a PTL=a GOTO2
```

Info:
```
// n, a, b, z     -> Setup string
// c, m, h        -> Constants
// MR, MP         -> Max Rod / Propellant <- Modify Propellant !
// d, e, f, g     -> :RodFuel buffer
// i, j, k, l     -> :Propellant buffer
// RD, PD         -> Rod / Propellant Difference (average of 3)
// RT, PT         -> Rod / Propellant Time (in second)
// RH, RM, PH, PM -> Rod / Propellant Hours/Minutes Left
// RTL, RTL       -> Rod / Propellant Time Left
// RP, PP         -> Rod / Propellant Percent
```
