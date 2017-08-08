# Ideas gathered during the Sardana training at Solaris

## Plugin system discovery based on modules

The plugin system could discover the plugin classes based on explicit declaration of modules to be scanned.
Instead of setting the `MacroPath` as a list of paths to be scanned, we could rather do the following:
```
MacroPath = ["my_pkg.macros.macro1", "my_pkg.macros.macros.macro2"]
```
or even:
```
MacroPath = ["my_pkg.macros"]
```
and let the Sardana scan all members of the module for those that are subclasses of the `Macro` class.

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

## Additional help for a controller class when you're defining one with `defctrl`
It would be great if when you type:
```
defctrl MyController ?
```
the help would show you all properties that should be filled for this controller class.

Additionally, if you use it for a pseudo controller, it could show all roles (separated between physical and pseudo) that are required for this pseudo controller class.

## `edctrl` and `edctrllib` to use Git as a VCS

If you make amendments to a controller (or a library of those), it would be great if it would automatically save the file and make a Git commit there (provided the controller is in a Git repository). That way you'd be able to keep track of every change that someone might make to your production controllers.

## Bug: `defelem` doesn't automatically increment axis number

When you try to add an element to a controller that already has elements and you don't specify the axis number, you might get an error. It looks like the automatic discovery of the lowest non-ocuppied axis number doesn't work.
