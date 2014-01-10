Race mode [mapname].routes file syntax documentation
========

The _routes_ file describes all the routes for the race mode of KTX on a specific map.

The file itself
--------

Every routes file needs to have the _mapname_ as filename and _.routes_. So a routes file for dm4 would be called dm4.routes.

Depending on the usage of red colored text and other gimmicks, you can or cannot save the file as unicode. If they are used, better encode the file in the Windows 1252 encoding, so your text does not get scrambled. For example the red '»' char used in the route descriptions is one of the bugged chars.

File syntax
--------
First of all, an example of a routes file, dm2.routes:

```
2

Ihm's quad run
highrlquadwaterlowerramh
35
1
1
7
1309.7 -903.8 344.0 5.2 87.8
1498.8 -713.5 184.0
1896.2 -634.4 184.0
2613.7 -218.5 120.0
2714.6 -1735.3 120.0
2445.9 -1979.4 120.0
2246.4 -2473.3 200.0

around dm2
waterquadlowrllowngstairs
35
2
1
7
2114.0 -100.9 24.0 -10.4 -109.4
2014.6 -469.5 140.7
1696.7 -1463.7 28.7
2612.7 -677.0 144.0
2304.8 -152.6 67.6
2397.6 86.0 41.2
2246.2 -194.7 -136.0
```

* Line 1: Number of routes defined in the file.
* Line 2/16: **Mandatory** empty line before every route definition.
* Line 3-15/17-29: A route definition.

A route defintion has the following syntax:

```
name
description
timeout time in seconds. value type is float, so decimal numbers are allowed.
weapon mode, 1 = no weapons allowed, 2 = weapons allowed, 3 = weapons allowed after 2 seconds
false start mode, 1 = no false start, 2 = false start
n: number of route nodes, including start and finish
start node definition: posx posy posz pitch yaw
n-2 checkpoint node definitions: posx posy posz
... some more checkpoints ...
finish node definition: posx posy posz
```

Notes
--------
* When you create your own routes ingame, the console shows you the coordinates for each one.
* Maybe you're wondering why for example _waterquadlowrllowngstairs_ is the description. Where are the spaces? Well, the red '»' is in undefined unicode ranges, so it is not displayed anywhere but in Quake. To input it (on windows) press ALT+0141. (Character 0x8D)
* For now, the number of routes and the number of nodes in a route are both restricted to 20. However, this seems to be an arbitrary limit, so it could be changed if needed. Testing has to be done on that, though.
* The up to now default routes are included in the `example-configs/ktx/race/routes` folder.