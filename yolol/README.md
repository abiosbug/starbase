Collection of Yolol scripts created for the Jilted from Singularity Starbase Community, designed by Sun-cy

### General yolol gotchas

#### Processing speed
Each yolol chip has a 0.2s line read speed. That means that every line will add .2 seconds to the total time needed to traverse the chip.  So if you need something updating fast, you can try to split your script over various chips so they all run as fast as possible.
Some scripts depend on the line read speed, eg. for calculating the current fuel or propellant consumption.  Keep this in mind when adjusting these.

#### Unitialized global variables and silent errors
Global variables are the variables available from your ship's internals.  They are always preceeded by a `:`. Local variables are only available in the current chip and cannot start with `:`.
When a yolol script tries to access a global variable that is not initialized, it will silently fail. You can test this by adding a GOTO at the end of the line and watch it being ignored.  Yolol chips cannot initialize global variables, you either need to assign them to a panel or button first.  If you don't want or don't have a panel or button, you have to add them to a Memory Chip instead.

#### to be continued..
