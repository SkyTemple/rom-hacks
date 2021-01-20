|logo|

"Explorers of Mud" - A Pokémon TTRPG highlight cutscene
=======================================================

|discord|

.. |logo| image:: https://raw.githubusercontent.com/SkyTemple/skytemple/master/skytemple/data/icons/hicolor/256x256/apps/skytemple.png

.. |discord| image:: https://img.shields.io/discord/710190644152369162?label=Discord
    :target: https://discord.gg/4e3X36f
    :alt: Discord

.. |kofi| image:: https://www.ko-fi.com/img/githubbutton_sm.svg
    :target: https://ko-fi.com/I2I81E5KH
    :alt: Ko-Fi

This is a cutscene, based on a `tabletop RPG campaign I'm in`_.

This repository contains the assets used to create the cutscene
and a guide on how to replicate it.

|kofi|

The cutscene
------------
This video shows the cutscene in action:
https://www.youtube.com/watch?v=08O1EZMeU7I

Credits
-------
Alolan Vulpix Sprite and Portrait by:
NeroIntruder - https://twitter.com/NeroIntruder

Bagon Portraits by:
C.Pariah

Script editing by Quilavabom and Icebelly.

Dock Tileset CC-BY-SA 3.0 Reid: https://opengameart.org/content/dock-tileset

How to apply the patch
----------------------
You can apply the patch ``mud.xdelta`` to a NA Explorers of Sky ROM using `XDelta`_.


How to re-create the cutscene
-----------------------------
Use a regular, unmodified game ROM for this.

You will need `SkyTemple`_ to-recreate the cutscene.

1. Change the starters
~~~~~~~~~~~~~~~~~~~~~~
Change the default starters.
The hero must be Riolu, the partner Vulpix. The name of the player is 'Nubi', the name of the partner 'Kiona'.

2. Change Vulpix and Bagon
~~~~~~~~~~~~~~~~~~~~~~~~~~
Change the Vulpix entry to have the type and ability of alolan Vulpix. Import the sprites
and portraits of Alolan Vulpix from SpriteBot (can be found on our Discord_).

For Bagon import its portraits from SpriteBot as well.

3. Recolor the Muk and Grimer sprites
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Recolor the sprites of Grimer and Muk to be brown (optional).

4. Apply the patch for Special Processes 51 and 52
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The Patches directory in this repository contains a patch that changes two special processes:
- 51: adds storage member ID 5 to the active roster
- 52: changes storage member ID 5's name to Arran

This is used to add Arran to the team. Place this patch in the Patches directory of the project directory,
then open SkyTemple and go to "ASM Patches" and apply the "PatchProcess51_and_52" patch and save.

Documentation for how this patch was created:
https://docs.google.com/document/d/1a4wmKbb-Iey2smit8nujpPxFPfJ8w44Ncyrfw7bq8eI/edit

5. Update the recruitment list
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1. Open SkyTemple and open "Ground Lists > Recruitment List"
2. Change entry 16 to: "Bagon (Male) ($0403)", Level 5, met at "??? (0214)"

6. Change the actor list
~~~~~~~~~~~~~~~~~~~~~~~~
The actor list defines which Pokémon can spawn on overworld maps.

1. Open SkyTemple and go to "ASM Patches".
   Apply the "ActorAndLevelLoader" patch and save.
2. Open "Ground Lists > Actors"
3. Change the following entries (make sure "Unk3" is "0" for all of them):

   - 69: Change the name to "NPC_CATERPIE" and the species to "Caterpie (Male) ($0010)"
   - 70: Change the name to "NPC_NUBI" and the species to "Riolu (Male) ($0489)"
   - 71: Change the name to "NPC_KIONA" and the species to "Vulpix (Female) ($0637)"
   - 72: Change the name to "NPC_ARRAN" and the species to "Bagon (Male) ($0403)"
   - 73: Change the name to "NPC_WURMPLE" and the species to "Wurmple (Male) ($0293)"
   - 74: Change the name to "NPC_WEEDLE" and the species to "Weedle (Male) ($0013)"
   - 75: Change the name to "NPC_LANDO" and the species to "Yanmega (Male) ($0511)"
   - 76: Change the name to "NPC_MUK" and the species to "Muk (Male) ($0089)"
   - 77: Change the name to "NPC_GRIMER1" and the species to "Grimer (Male) ($0088)"
   - 78: Change the name to "NPC_GRIMER2" and the species to "Grimer (Male) ($0088)"

7. Apply the map backgrounds
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

D01P11A
#######
1. Use the search function of SkyTemple to open the map background "D01P11A" (NOT the scene!).
2. In the toolbar open "Map > Width and Height" and set the width and height to 40x30 chunks.
3. In the toolbar open "Map > Import Layers from Image..."
4. Select the "D01P11A_layer1.png" from the "MapBG" directory you downloaded as the Layer 1 image.
5. Select the "D01P11A_layer2.png" from the "MapBG" directory you downloaded as the Layer 2 image.
6. In the toolbar open "Palettes > Animation Settings" and set "Enable Palette Animation" to off.
7. Close the dialog with "Apply".

D01P11B
#######
1. Use the search function of SkyTemple to open the map background "D01P11B" (NOT the scene!).
2. In the toolbar open "Map > Width and Height" and set the width and height to 12x9 chunks.
3. In the toolbar open "Map > Import Layers from Image..."
4. Select the "D01P11B_layer1.png" from the "MapBG" directory you downloaded as the Layer 1 image.
5. Select the "D01P11B_layer2.png" from the "MapBG" directory you downloaded as the Layer 2 image.
6. In the toolbar open "Palettes > Animation Settings" and set "Enable Palette Animation" to off.
7. Close the dialog with "Apply".

8. Create the scenes for the cutscene
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

D01P11A
#######
1. In the SkyTemple main UI search for "M01A0103" and open the
   scene "D01P11A > Acting (ssa) > m01a0103".
2. Arrange the sceene as shown in the images "m01a0103.png" and "m01a0103_zoom.png". Make sure you place the actors
   on the correct sectors (layers), you may need to create new sectors.
3. In the SkyTemple main UI search for "M12A1201" and open the
   scene "D01P11A > Acting (ssa) > m12a1201".
4. Arrange the sceene as shown in the image "m12a1201.png". Make sure you place the actors
   on the correct sectors (layers), you may need to create new sectors.

D01P11B
#######
1. In the SkyTemple main UI search for "M01A0102" and open the
   scene "D01P11B > Acting (ssa) > m01a0102".
2. Arrange the sceene as shown in the image "m01a0102.png". Make sure you place the actors
   on the correct sectors (layers), you may need to create new sectors.
   The blue arrow is the performer. "PLAYER", "ATTENDANT1" and "UNIT_NPC1" are all placed on top of each other on the left.

9. Create the scripts for the scene and an entrypoint to load it
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Open the SkyTemple Script Engine Debugger, by pressing the bug icon in the top right.

Macros
######
Copy the Macros directory into the project directory and restart SkyTemple.

unionall.ssb
############
Open the script "Common > unionall.ssb". Search for ``coro EVENT_DIVIDE {``.

In the lines after that insert::

    debug_Print('Custom Cutscene');
    ProcessSpecial(PROCESS_SPECIAL_INIT_MAIN_TEAM_AFTER_QUIZ, 0, 0);
    ProcessSpecial(PROCESS_SPECIAL_SET_TEAM_SETUP_HERO_AND_PARTNER_ONLY, 0, 0);
    ProcessSpecial(PROCESS_SPECIAL_ADD_RECRUITABLE_TO_TEAM, 16, 0);
    // THE FOLLOWING LINES REQUIRE THE PATCH TO BE APPLIED!
    ProcessSpecial(52, 0, 0);
    ProcessSpecial(51, 0, 0);

    CallCommon(CORO_SUBSCREEN_INIT);
    supervision_ExecuteActingSub(LEVEL_D01P11B, 'M01A0201', 0);
    supervision_ExecuteActingSub(LEVEL_D01P11A, 'M01A0103', 0);
    end;

Search for ``coro GETOUT_SCENARIO_DUNGEON`` in the script.

Replace the beginning of the coroutine with this (up to the first ``case 3:``::

    debug_Print('GETOUT_SCENARIO_DUNGEON');
    CallCommon(CORO_RESCUE_SET);
    switch ( $GROUND_START_MODE ) {
        case 8:
            debug_Print('DUNGEON_GETOUT_CONQUEST');
            if ( variation ) {
                §label_636;
                dungeon_mode(3) = DMODE_OPEN_AND_REQUEST;
                JumpCommon(CORO_EVENT_M02_09_10);
            } else {
                switch ( $DUNGEON_ENTER ) {
                    case 0:
                    default:
                        JumpCommon(CORO_EVENT_DIVIDE);
                    case 1:
                        if ( scn($SCENARIO_MAIN) == [2, 2] ) {
                            JumpCommon(CORO_EVENT_M01_04);
                        } elseif ( scn($SCENARIO_MAIN) == [2, 3] ) {
                            JumpCommon(CORO_EVENT_M01_05);
                        } else {
                            hold;
                        }
                        break;
                    case 2:
                        CallCommon(CORO_SUBSCREEN_INIT);
                        supervision_ExecuteActingSub(LEVEL_D01P11A, 'M12A1201', 0);
                        end;

m01a0201.ssb, m01a0103.ssb and m12a1201.ssb
###########################################
Use the search function of the debugger to locate the script "D01P11A > Acting (ssa) > m01a0103.ssb".
Replace the entire content of that file with the file "SCRIPT/D01P11A/m01a0103.exps" in this repository.
Hit CRTL+S to save.

Use the search function of the debugger to locate the script "D01P11B > Acting (ssa) > m01a0201.ssb".
Replace the entire content of that file with the file "SCRIPT/D01P11B/m01a0201.exps" in this repository.
Hit CRTL+S to save.

Use the search function of the debugger to locate the script "D01P11A > Acting (ssa) > m12a1201.ssb".
Replace the entire content of that file with the file "SCRIPT/D01P11B/m12a1201.exps" in this repository.
Hit CRTL+S to save.

10. Import the boss fight background
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1. Navigate to "Dungeon Tilesets > Background 170"
2. In the menu bar select "Background > Import Background from Image..."
3. Import "DungeonBG/170.png"
4. Under "Palettes > Animation Settings" disable animations for both palettes and apply.

11. Create the fixed floor for the boss fight
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Create the bosses
#################
1. Navigate to "Fixed Rooms"
2. Select the Pokémon Tab
3. Change the following entries:

21: Grimer (Male) ($0088) | 6: Strong Enemy | Stats: 1
22: Muk (Male) ($0089) | 6: Strong Enemy | Stats: 2
23: Grimer (Male) ($0088) | 6: Strong Enemy | Stats: 1

Create the floor
################
1. Navigate to "Fixed Rooms > Fixed Room 1"
2. Arrange it as shown in "fixed_room1.png", the Muk and Grimer entities are the ones configured above.

12. Apply some additional patches
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1. Open SkyTemple and go to "ASM Patches".
   Apply the "MoveShortcuts" and "DisableTips" patches and save.

Done!
~~~~~
You are now done! Fire up the game in an emulator and select "New Game" or "Continue" and the
cutscene will play.

.. _tabletop RPG campaign I'm in:    https://www.youtube.com/channel/UCtkIQ9EQlq-n7YRg7p0vAeA
.. _XDelta:                 https://www.romhacking.net/utilities/598/
.. _SkyTemple:              https://projectpokemon.org/home/forums/topic/57303-pmd2-skytemple-rom-editor-maps-scripts-debugger/
.. _skytemple-files:        https://pypi.org/project/skytemple-files/
.. _Discord:                https://discord.gg/4e3X36f
