# Ideas gathered during the Sardana training at Solaris

## Plugin system discovery based on modules

The plugin system could discover the plugin classes based on explicit declaration of modules to be scanned.

## Inheritance between the plugin classes is possible if the plugin classes are just defined in the PoolPath and not in the PythonPath

More preciselly the plugin classes needs to be defined in two different path of the PoolPath.
Lets say that class `Foo` is defined in the lower order path than class `Bar`. Than class `Bar` can inherit from class `Foo`.
This should be verified and checked if we could documment it as a proper way of making the plugin class inheritance or we call it as a side effect.

## `relmaclib` & `addmaclib`

It is painfull for the users to have to call the `addmaclib` macro when previously the `relmaclib` failed e.g. due to the syntax error and the library was eliminated from system.
Then, if we want to try to reload the module adain, we have to use the `addmaclib` macro.

## `edmac` could add a new module to the system

If a path is not present in the `MacroPath` it is not possible to add a macro module located in this path to the system using the `edmac`

## Documentation abou the core should be written

* Class diagrams describing the most relevant parts of the core could be added to the documentation (developers).
* The core python modules could be better documented (docstrings).

## Is it possible to merge somehow easilly the Tango loggin and Sardana logging?

## How to properly use Sardana with the new Tango archiving system (HDB++)

* Use the Facade to push the archiving events
* Push the archiving events from the code (Tango layer only)

## Would it be interesting make optional use of the critieria when pushing Tango events

## It would be interesting to implement move of the motors in fully synchronized way
i.e. equal accaleration and deceleration times and proportional velocities so the top velocity time is equal on all motors. 

## It could be interesting to access the 0D's beffers in the pseudo counters, how to do it properly?

## It could be interesting to access the backlash value in the motor controller plugin.
