Fortress Blast maps repository
==============================

This repository contains additional map support that the base version of Fortress Blast does not come with. You can pick and choose .json files from this repository to add to your server, depending on what maps you have in rotation. If you cannot find the map you need support for, you can create a .json file yourself and fork this repository in order to send a pull request that will be manually reviewed.

[Download the Fortress Blast plugin here](https://github.com/Fortress-Blast/Fortress-Blast)

How to create a .json file
--------------------------

The following are instructions on how to make a .json file as described above.

1. If you don't have a .vmf version of the map you want to support, decompile the map's .bsp fie using [BSPSource](https://github.com/ata4/bspsrc/releases).
2. Open the .vmf in Hammer (found in *steamapps/common/Team Fortress 2/bin/hammer.exe*).
3. Select the **Entity Tool** on the left pane, change the value of the **Objects** box in the right pane to `info_powerup_spawn` and click somewhere in the 3D view to place it down.
4. Repeat step 3 but for `info_null`.
5. Using the 2D views, move these two entities so that both of their origins are at the same point in 3D space. You should try to keep the entities as close to the ground as possible without seeing the outlined bounding box going through the floor or any walls.
6. Use a combination of cutting, copying and pasting to place these two entities in several positions around the map. Make sure that you move both at the same time, otherwise they will become out of sync. If the map has rotational or mirror symmetry, only place the entities on one side of the map.
7. Create a .json file with the name of the map in question. Have three lines: `{` in the first, a `}` in the second and nothing in the third.
8. If you want to order the coordinates in your .json file, use the 3D view to fly around the map and click on the small box (info_null) underneath each info_powerup_spawn you placed (do not select the powerups). If you are not concerned about order, select **Map > Entity Report...** in the topbar, and check the box that says **By class**, typing `INFO_NULL` into the box beneath it, and clicking on each entry one by one.
9. As you click through each info_null, you will see a string in the bottom-right corner of Hammer that reads something like `0w 0l 0h @(0, 0, 0)`. The three values in the brackets are the X, Y and Z coordinates for that powerup. Add a new line inbetween the curly brackets of the .json for each info_null, specifying their order and coordinates like so: `"5-x": "123.0", "5-y": "-1337.0", "5-z": "0.0",` (Do not include a comma at the end if it is the last powerup).
10. If the map has symmetry, add `"flipx": false, "flipy": false, "centerx": "0.0", "centery": "0.0",` before all the coordinates. Set the X and Y coordinates of the center of the map, and specify whether the map should flip by X or Y (mirror) or both (rotational).
