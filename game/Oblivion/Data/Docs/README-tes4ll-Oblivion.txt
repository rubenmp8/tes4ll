Important:

!!! Before your start, please make a backup of your meshes in Data\meshes\landscape\lod, and Data\textures\landscapelod\generated !!!

Overview
========
This tool creates landscape LOD meshes based on the landscape heightmap. Therefore, it can be used to replace the landscape meshes of Oblivion including all the additional changes added by the mods. 

Moreover, a configuration file (multi purpose batch file) with a command list allows to control the behavior of vertex setting and calculation completely, up to the placement of single vertices.

Author
======
gruftikus@"nexusmods"

Why?
====
In Oblivion, the LOD meshes can be replaced quad-by-quad only. If one has a lot of landscape changes (like UL or Elsweyr Anequina), the following problems may appear:

* The quad meshes do not fit at their borders, because they were created independently

* "Wall-like" steps between the normal grid and the LOD meshes

* Floating objects (trees, buildings)

Requirements
============
None.

But this is not true: 

* If you want to use a different dds tool (by default it is S3TC.exe), you have to download such a tool. E.g. nconvert: http://www.xnview.com/de/nconvert.html or nvdxt: http://developer.nvidia.com/content/legacy-texture-tools

* If you need a GUI, use MPGUI (http://oblivion.nexusmods.com/mods/41447).

Installation
============
Unpack the tes4ll 7z-archive and move the content into the data directory of Oblivion. When asked, merge the ini-directory of tes4ll into your ini.

After this procedure you should have one executable in your Oblivion data directory (tes4ll.exe), several windows bat-files (tes4ll_*.bat), and the files which came with TES4qLOD (see Readme-TES4qLOD.rtf)

Uninstallation
==============
Restore the old LOD meshes in Data\meshes\landscape\lod which you (hopefully!) saved. Delete tes4ll.exe, and the content of ini\tes4ll

Generation of meshes (the simple method)
========================================

Actually, there are 2 simple methods:

1. Start the one of the Windows-bat-files by double clicking on it. 

At the moment, 3 versions are supported:

"tes4ll_ultimate.bat" -> "Ultimate resolution", 18000 vertex points, and a very detailed wall remover (something for high-end graphics cards)
"tes4ll_highres.bat" -> "High resolution", 13000 vertex points (leads to 80% more triangles as Vanilla)
"tes4ll_midres.bat"  -> "Mid  resolution", 10000 vertex points (leads to 20% more triangles as Vanilla)

This overwrites your LOD files (hey, did you made a backup?)

The generation can take some time (10-20 minutes). In particular, after calling the Delaunay Triangulation part it seems that the program does not continue. Please have some patience.

2. Tes4ll is compatible to my MPGUI. In order to use the GUI, you first must install MPGUI. After installation, you can either double-click on one of the *.mpb files in ini\tes4ll, or start MPGUI and open one of the files. With MPGUI you can save you complete configuration of you want. For details of operation, please open the help documents of MPGUI.

Normalmaps
==========
Tes4ll can also produce normalmaps. Use tes4ll_normalmaps.bat for this purpose. Change the "1.0" in z_val=1.0 to 2-0 or 4.0 if you want to have more contrast. Add "lodshadows" in the flag list, if you would like to have the "terrain shadows" (see http://oblivion.nexusmods.com/mods/41243).

TES4qLOD
========
In order to enable the optional call of tes4qlod, add the flags "tes4qlod,qlod1,option_blending" to the list of flags (the argument list after the '-f') in one of the windows bat-files mentioned above. 

You can also use tes4ll_tes4qlod.bat. This bat-file produces only the color maps in 1024x1024 resolution. If you want 2048x2048 or 4096x4096, change "qlod1" to "qlod2" or "qlod4", respectively.

I recommend the 1024x1024 version, because it has less tiling.

Generation of meshes (expert modus)
===================================
Adapt the configuration file for your needs. A detailed manual of the commands can be found at github:
https://github.com/Gruftikus/tes4ll/blob/master/REFERENCE_MANUAL-tes4ll.pdf?raw=true
There are many things possible, tes4ll is highly adaptable. The details of this goes beyond this README. If you are in trouble, please contact me.

Known issues
============
* With a single lod mesh (i.e. one quad) it is not possible to go above 65535 triangle points. Although I use the best stripification algorithm which is on the market, this limits the number of vertex points. There is no way to calculate the number of triangle points in advance by the number of vertex points. If you reach the limit, reduce the number of vertex points per quad.

The shape version can use up to 65535 triangles (the ultimate version stays well below this value)

* Sometimes, when the water is shallow, the coast line is not sampled correctly. I tried hard to have some automatic algorithms to avoid this, but not yet found a good solution. The best is to repair it by hand (with SetVertex)

Writing data files
==================
Nothing is perfect - also not the algorithms in tes4ll. If you still find walls, floating trees etc, you can go with your player character to the place, and get the position by opening the console and typing 'tdt'.

These positions can be written into a data file which contains a list of x,y positions (x and y separated by a space).

This data file can be added to the batch file (e.g. tes4ll_all.mpb).

Rerun tes4ll - and the additional vertices should cure the problem.

Credits
=======
Thanks to all users for testing and suggestions, in particular Auryga and Supierce for testing the program.

License
=======
Copyright (C) 2011-2012
This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see http://www.gnu.org/licenses/.