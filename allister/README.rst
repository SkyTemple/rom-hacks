|logo|

"Allister" - A PMD&D highlight cutscene
=======================================

|discord|

.. |logo| image:: https://raw.githubusercontent.com/SkyTemple/skytemple/master/skytemple/data/icons/hicolor/256x256/apps/skytemple.png

.. |discord| image:: https://img.shields.io/discord/710190644152369162?label=Discord
    :target: https://discord.gg/4e3X36f
    :alt: Discord

.. |kofi| image:: https://www.ko-fi.com/img/githubbutton_sm.svg
    :target: https://ko-fi.com/I2I81E5KH
    :alt: Ko-Fi

This is a highlight from session #40 of `TheGoldCrow's PMD&D`_.

This repository contains the assets used to create the cutscene
and a guide on how to replicate it.

|kofi|

The cutscene
------------
This video shows the cutscene in action:
https://youtu.be/R-skitzo6sg

Credits
-------
Litten sprite by NeroIntrouder:
https://twitter.com/nerointruder

Lucius portraits by Fireally:
https://www.youtube.com/channel/UCslMDS9pAH-ay6qqKlyyJzw

Henry and Raffa portraits by Quil.

Wooden ship tiles by Tuomo Untinen:
CC BY 3.0: https://opengameart.org/content/lpc-wooden-ship-tiles

How to apply the patch
----------------------
You can apply the patch ``allister.xdelta`` to any US/NA Explorers
of Sky ROM using `XDelta`_.


How to re-create the cutscene
-----------------------------
Use a regular, unmodified game ROM for this.

You will need `SkyTemple`_ to-recreate the cutscene. PLEASE NOTE
that for some of these things, SkyTemple 0.1.0 may be needed,
which isn't released yet (at the time of writing).
You can get it by applying for the "Beta Tester" role on the
SkyTemple Discord server.

1. Change the actor list
~~~~~~~~~~~~~~~~~~~~~~~~
The actor list defines which Pokémon can spawn on overworld maps.

1. Open SkyTemple and go to "ASM Patches".
   Apply the "ActorAndLevelLoader" patch and save.
2. Open "Ground Lists > Actors"
3. Change the following entries (make sure "Unk3" is "0" for all of them):

   - 69: Change the name to "DH_LUCIUS" and the species to "Lopunny (Male) ($0469)"
   - 70: Change the name to "DH_HENRY" and the species to "Elekid (Male) ($0266)"
   - 71: Change the name to "DH_RAFFA" and the species to "Shinx (Female) ($1038)"
   - 72: Change the name to "DH_ODRICK" and the species to "Charmeleon (Male) ($0005)"
   - 73: Change the name to "DH_ALLISTER" and the species to "Sandslash (Male) ($0028)"

2. Change the Pokémon names and import the portraits
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Make sure you have the "Portraits" directory in this repository downloaded, we will use it now.
Use the search function in SkyTemple to locate the Pokémon.

- Change Pokémon "Lopunny #469" (Male). Change the name to "Lucius". Go to portraits, click "Import" and
  select the "Portraits" directory you downloaded.
- Change Pokémon "Elekid" (Male). Change the name to "Henry". Go to portraits, click "Import" and
  select the "Portraits" directory you downloaded.
- Change Pokémon "Shinx" (Female). Change the name to "Raffa". Go to portraits, click "Import" and
  select the "Portraits" directory you downloaded.
- Change Pokémon "Charmeleon" (Male). Change the name to "Odrick".
- Change Pokémon "Sandslash" (Male). Change the name to "Allister".

3. Apply the continue-screen progress icons
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Make sure you have the "W16" directory in this repository downloaded, we will use it now.

1. Go to "Misc Graphics > FONT/clrmark1.w16"
2. Click on "Import" and select the "W16" directory you imported.

4. Apply the map background for the top-screen island image
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Make sure you have the "MapBG" directory in this repository downloaded, we will use it now and for
the next step.

1. Use the search function of SkyTemple to open the map background "V02P01A"
2. In the toolbar open "Map > Width and Height" and make sure the map has a width and height of 13x10 chunks.
3. In the toolbar open "Map > Import Layers from Image..."
4. Select the "V02P01A_layer1.png" from the "MapBG" directory you downloaded as the Layer 1 image.
5. Select the "V02P01A_layer2.png" from the "MapBG" directory you downloaded as the Layer 2 image.

5. Apply the map background for the island and ship
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1. Use the search function of SkyTemple to open the map background "D01P11A" (NOT the scene!).
2. In the toolbar open "Map > Width and Height" and set the width and height to 13x10 chunks.
3. In the toolbar open "Map > Import Layers from Image..."
4. Select the "D01P11A_layer1.png" from the "MapBG" directory you downloaded as the Layer 1 image.
5. Select the "D01P11A_layer2.png" from the "MapBG" directory you downloaded as the Layer 2 image.
6. In the toolbar open "Palettes > Animation Settings" and make sure ALL fields are "0" (don't apply yet).
7. For "Palette 5" select a "Frame Time" of "13" and a "# of Frames of 17".
8. Close the dialog with "Apply".


6. Apply the title screen background image
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Make sure you have the "BGP" directory in this repository downloaded, we will use it now.

1. Go to "Backgrounds > BACK/s09pXXa.bgp", where XX is a number between 01 and 10 (repeat both steps for all).
2. In the toolbar select "Background > Import..." and use the "titlescreen.png" from the "BGP" directory
   you downloaded.

7. Create the scene for the cutscene
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1. In the SkyTemple main UI search for "M01A0103" and open the
   scene "D01P11A > Acting (ssa) > m01a0103".
2. Arrange the sceene as shown in the image "m01a0103.png". Make sure you place the actors
   and objects on the correct sectors (layers). You may need to delete some, in the end it should be 3.
   The blue arrow is the performer. The book and water splash are objects, the Pokémon are actors.

8. Create the scripts for the scene and an entrypoint to load it
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Open the SkyTemple Script Engine Debugger, by pressing the bug icon in the top right.

unionall.ssb
############
Open the script "Common > unionall.ssb". Search for ``coro EVENT_DIVIDE {``.

In the line after that insert::

    supervision_ExecuteActingSub(LEVEL_D01P11A, 'M01A0103', 0);

m01a0103.ssb
############
Use the search function of the debugger to locate the script "D01P11A > Acting (ssa) > m01a0103.ssb".

Replace the entire content of that file with the file "SCRIPT/D01P11A/m01a0103.exps" in this repository.
Hit CRTL+S to save.

9. Apply the Litten sprite
~~~~~~~~~~~~~~~~~~~~~~~~~~
Save your changes in SkyTemple and close it.

Apply the sprite in "Sprite/321_litten.wan" of this repository as file #321 in the file
"MONSTER/m_ground.bin" in the ROM file.

I have sadly absolutely no idea how to do this using a tool. I used this Python script to do it:

.. code-block:: python

    from ndspy.rom import NintendoDSRom

    from skytemple_files.common.types.file_types import FileType

    rom = NintendoDSRom.fromFile('allister.nds')

    m_ground = rom.getFileByName('MONSTER/m_ground.bin')

    with open('Sprite/321_litten.wan', 'rb') as f:
        mg = FileType.BIN_PACK.deserialize(m_ground)
        mg[321] = f.read()
        m_ground_new = FileType.BIN_PACK.serialize(mg)
        rom.setFileByName('MONSTER/m_ground.bin', m_ground_new)

    rom.saveToFile('allister.nds')

To use this, you need to install the Python library `skytemple-files`_. Replace the ROM
filename and the path to the WAN file in this repository with your own!

Done!
~~~~~
You are now done! Fire up the game in an emulator and select "New Game" or "Continue" and the
cutscene will play.

.. _TheGoldCrow's PMD&D:    https://www.youtube.com/thegoldcrow
.. _XDelta:                 https://www.romhacking.net/utilities/598/
.. _SkyTemple:              https://projectpokemon.org/home/forums/topic/57303-pmd2-skytemple-rom-editor-maps-scripts-debugger/
.. _skytemple-files:        https://pypi.org/project/skytemple-files/
