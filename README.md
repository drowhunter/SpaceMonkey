# SpaceMonkey - Open Source Telemetry Provider.

SpaceMonkey was created to be a telemetry interface for games with no native telemetry support. 

SpaceMonkey mimics the functionality of the Codemasters Dirt 4 custom udp format which allows SpaceMonkey to be used via the UDP protocol by any software that already supports Dirt 4 and Dirt Rally 2.0 custom udp.
SpaceMonkey also optionally writes telemetry to a Memory Mapped File as an alternative to UDP.

SpaceMonkey contains telemetry visualisation and filtering functionality.

SpaceMonkey supports XINPUT, currently mapped to standard gamepad inputs for steering (left stick), accelerator(right trigger), and brake(left trigger). Clutch and axis assignments coming in a future version. Use the XBOX 360 controller emulator to map your direct input devices to an XINPUT gamepad. https://www.x360ce.com/

SpaceMonkey has been tested with Sim Racing Studio (motion, wind, shakers and led), SimCommander 4 (Accuforce v2) and SimFeedback (motion) and should work with any software that supports Dirt 4 Custom UDP.

```diff
- Please make sure you run SpaceMonkeyStart.exe as administrator or use a user account with administrator privileges.
```

### Supported Games

- Dirt 5
- Wreckfest
- BeamNG.Drive
- GTA 5
- Digital Combat Simulator
- Nascar Heat 4/5 (MonsterGames)
- All American Racing (MonsterGames)
- Sprint Car Racing (MonsterGames)
- WRC 7/8/9
- Richard Burns Rally (NGP 6)
- STAR WARS: Squadrons (Note: broken; requires pointer change)
- Warplanes: WW1
- VTOL VR
- IL-2 Sturmovik
- Overload
- Trail Out
- Mechwarrior 5 Mercenaries
- Dakar Desert Rally
- WRC Generations
- Tiny Combat Arena
- EA Sports WRC
- UEVR
- Wreckfest 2


## Installation

1. Download the latest release of SpaceMonkey from https://github.com/PHARTGAMES/SpaceMonkey/releases
2. Extract anywhere to your local drive.
3. Run Register.bat as administrator.


## Main Interface


![Main Interface](https://github.com/PHARTGAMES/SpaceMonkey/blob/main/Documentation/MainInterface.png?raw=true))]

1. Game selection buttons; press one to load the interface for the selected game.
2. Config selection; Choose or duplicate/rename the main configuration parameters. Configs are stored in the Configs folder. Ideally a config file will be created for each game as they often have different requirements for filtering.
3. Filter Config; Extra filter configs can be created by copying a filter config in the Filters folder.
4. Telemetry Ouput; Choose how you want telemetry to be output from SpaceMonkey. These configs are modified by pressing the Outputs button (6)
5. Hotkey;  The hotkey can be used to pause and resume telemetry globally when the app is not in focus.
6. Outputs; Press this button to load the Outputs interface.
7. Filters; press this to load the filters interface.
8. Haptics; press this to load the haptics interface.


All changes to config options are saved as they are changed.


## Outputs Interface


![Outputs Interface](https://github.com/PHARTGAMES/SpaceMonkey/blob/main/Documentation/OutputsInterface.png?raw=true))]

The outputs interface modifies the outputs config that is selected in the main interface. 
Only load this interface while a game ui is not running.

1. Change the dropdown to select an output type then press the Add Output button to add an output. Callback is a reserved type that currently only works with Simfeedback and any other software that wants to use this interface. It doesn't need to be added manually and can be ignored for now.
2. Output MMF outputs the 'Packet Format' specified, to the Memory Mapped File with the name specified in 'MMFName', using the global mutex specified by 'MMFMutexName'. The values shown here are the defaults used by existing software.
3. Output UDP outputs the 'Packet Format' specified, over UDP to the 'UDP IP' specified and and 'Port' specified. The example here outputs the Codemasters extradata=3 format which is what most software uses for dirt rally and dirt rally 2.
4. 'Packet Format Destinations'; these are folders that the packet format configuration file is copied to. Packet formats are specified in the PacketFormats folder and conform to the Dirt 4 Custom UDP specification. https://www.scribd.com/document/350826037/UDP-output-setup

The default output configs are as follows

1. default_CB: This can be specified when you just want to output in the default format via callback. This is primarily used when SpaceMonkey is loaded as a dll from inside some other app and registers a callback to recieve telemetry that way. This is now the preferred method for SimFeedback as it has the lowest latency.
2. default_CMED3: This config is to output to Codemasters extradata=3 format for when you want to output to software that supports this specific format for Dirt Rally 1/2 and it doesn't support custom udp. SimHub is one example. 
3. default_MMF_UDP: This can be specified when you want to output to both MMF and UDP with the default formats as SpaceMonkey has always done by default.
4. default_MMF_UDP_CMED3: This can be specified when you want to output to MMF with the default format, and then also output Codemasters extradata=3 over UDP to some other app such as SimHub.


---

# Games

## DIRT5

### Usage

1. Load Dirt 5 and get to the main menu with the vehicle visible.
2. Go to the main interface of Space Monkey and select a main config for DIRT5.
3. Go to the main interface of Space Monkey and press the DIRT5 button.
4. Click the Initialize! button in the SpaceMonkey Dirt5UI and wait for the game's memory to be scanned. If successful the status message will change to Success! and you will see debug output in the text box.
5. SpaceMonkey will now be outputting telemetry.


---

## Wreckfest

### Usage

1. Load Wreckfest in 64 bit mode.
2. Setup a session and get to the stage where you have the start race option on the left and the selected vehicle in the centre of the screen.
3. Go to the main interface of Space Monkey and select a main config for Wreckfest.
4. Go to the main interface of Space Monkey and press the Wreckfest button.
5. Select the player number from the drop down. In single player this is always 00. In multiplayer this is the order of your player in the lobby at the point that you join the lobby. Check as soon as you enter the lobby or you may get the wrong number.
6. Click the Initialize button and wait for the game's memory to be scanned. If successful the status message will change to Success! and you will see debug output in the text box.
7. Space Monkey will now be outputting telemetry.


---

## Wreckfest 2

### Usage (Single Player)

1. Load Wreckfest 2.
2. Setup a session and get to the stage where you have the START option on the left and the selected vehicle in the centre of the screen. (session start menu)
3. Go to the main interface of Space Monkey and select a main config for Wreckfest 2.
4. Go to the main interface of Space Monkey and press the Wreckfest 2 button.
5. Select a value for Max Cars. This is the number of cars to search for, setting this to 1 will just find the first car and is a quicker Scan for solo play with no ai. Max Cars set to 24 will find up to 24 cars if your grid size is set to 24, if grid size is not set to 24 you may find some garbage also.
6. Click the Scan button and wait. You only need to Scan as many times as you change the grid size in the game settings and/or Max Cars in Wreckfest2UI.
7. Once the Scan is complete select your car in the dropdown on the right. Knowing which car is yours can be tricky but this can also be changed after initialization. If you do a single player race with 1 car and Max Cars set to 1 you can know the number of your car because it's the only car that will show in the results. Once you know this number you can use it in other races with bigger grids as long as you don't change the car type and don't restart the entire application. You can also infer which car is yours by changing the Selected Car dropdown after initialization and looking at the speed value in the debug window; if you're stopped, speed will be almost 0. You can also infer which car is yours by 
8. Click the Initialize button to start sending telemetry.


### Usage (Multiplayer)

1. Go to the main interface of Space Monkey and select a main config for Wreckfest 2.
2. Go to the main interface of Space Monkey and press the Wreckfest 2 button.
3. Load Wreckfest 2.
4. Join multiplayer and wait for the session to start.
5. In the Wreckfest2UI select a value for Max Cars, whatever the grid size is for the session.
6. Click the Scan button and wait, this could take longer than an entire race.. 
7. Once the Scan is complete select your car in the dropdown on the right. Knowing which car is yours can be tricky but this can also be changed after initialization. Once you have found your car number you can continue using it as long as you stay in the same session, don't change vehicles or track.
8. Click the Initialize button to start sending telemetry.

### Finding my car

- Often it's the first car in the list after a clean start as long as you don't change cars.
- Look in the debug window for the speed, match this speed to your actual speed.
- In single player on the session start menu, look at the yaw value in the debug window; your car will have a yaw of approximately -2, all others will be almost 0. (I haven't automated this because it's not the case in multiplayer).

---

## BeamNG.Drive

### Setup

1. Backup your motionSim.lua file in the lua/vehicle subfolder of BeamNG.drive.
2. Run the SpaceMonkey BeamNG.Drive plugin.msi installer in the BeamNG subfolder of Space Monkey to install the BeamNG.Drive telemetry provider into BeamNG.Drive. NOTE: installer in 1.0.6 is broken, please use this one https://github.com/PHARTGAMES/SpaceMonkey/blob/main/BeamNG/Installer/SpaceMonkey%20BeamNG.Drive%20plugin-SetupFiles/SpaceMonkey%20BeamNG.Drive%20plugin.msi
3. Within BeamNG.drive 'Options > OTHER', set the following options:

- MotionSim enabled [x]
- IP: 127.0.0.1
- Port: 4444
- Update rate: 50
- Acceleration Smoothing: X, Y, Z all set to 0. (This is a personal preference, however these values are also programatically smoothed within the plugin code.)

### Usage

1. Go to the main interface of Space Monkey and select a main config for BeamNG Drive.
2. Go to the main interface of Space Monkey and press the BeamNG Drive button.
3. Specify the UDP receive port specified in the setup step (Default 4444)
4. Press the Initialize! button.
5. Space Monkey will now wait for a connection from BeamNG.Drive and output telemetry automatically. You can launch BeamNG.Drive and any other software at this point.

---

## EA Sports WRC

### Setup

1. Navigate to Documents/My Games/WRC/telemetry/
2. Edit the config.json file in a text editor
3. Change the "structure": "wrc" entry to match as follows; frequencyHz and port are optional

```json
{
	"structure": "wrc",
	"packet": "session_update",
	"ip": "127.0.0.1",
	"port": 20777,
	"frequencyHz": 60,
	"bEnabled": true
}
```


### Usage

1. Go to the main interface of Space Monkey and select a main config for EA WRC.
2. Go to the main interface of Space Monkey and press the EA WRC button.
3. Specify the UDP receive port specified in the setup step (Default 20777), if you are forwarding to a different port with SimHub or other, use this port.
4. Press the Initialize! button.
5. Space Monkey will now wait for a connection from EA Sports WRC and output telemetry automatically. You can launch EA Sports WRC and any other software at this point.

---

## GTAV

### Setup

1. Install ScripthookV: https://www.gta5-mods.com/tools/script-hook-v
2. Download and install Community Script Hook V .NET: https://www.gta5-mods.com/tools/scripthookv-net
3. Run the "SMTP GTA Plugin.msi" installer in the GTAV subfolder of SpaceMonkey. Install into your GTAV root folder, the default location is appropriate for a default steam installation, just need to change the drive letter.

### Usage

1. Go to the main interface of Space Monkey and select a main config for GTAV.
2. Go to the main interface of Space Monkey and press the GTAV button.
3. Press the Initialize! button.
4. Space Monkey will now wait for a connection from GTAV and output telemetry automatically. You can launch GTAV and any other software at this point.

---
## Digital Combat Simulator

### Setup

1. Backup any Export.lua files in your C:\Users\USER_NAME\Saved Games\DCS\Scripts\
2. Run the "SMTP DCS Export Plugin.msi" installer in the DCS subfolder of SpaceMonkey. Install into your C:\Users\USER_NAME\Saved Games\DCS\Scripts folder, the default destination should be appropriate.
3. If you are using multiple export files, you can remove the SpaceMonkey Export.lua and add a "dofile(lfs.writedir()..[[Scripts\ExportSM.lua]])" entry to your main Export.lua.

### Usage

1. Go to the main interface of Space Monkey and select a main config for DCS.
2. Go to the main interface of Space Monkey and press the DCS button.
3. Specify the UDP receive port specified in the setup step (Default 6666). If you want to recieve on a different port you will also need to edit the Export.lua file installed to C:\Users\USER_NAME\Saved Games\DCS\Scripts\ and change the port.
4. Press the Initialize! button.
5. Space Monkey will now wait for a connection from DCS and output telemetry automatically. You can launch DCS and any other software at this point.

---


## Nascar Heat 4/5, All American Racing and Sprint Car Racing.

### Usage

1. Load the game.
2. Go to the main interface of Space Monkey and select a main config for MonsterGames..
3. Go to the main interface of Space Monkey and press the Nascar Heat 4/5..etc.. button which will load the MonsterGamesUI.
4. In the Monster Games UI, click the Initialize button and wait for a message box to appear in the top left corner of the game window stating that SpaceMonkey is injected.
5. Space Monkey will now be outputting telemetry. Load any other software at this point.

---
## WRC 7/8/9

### Warning

This feature only outputs Sway, Heave and Surge accelerations and may not perform optimally. As such, the output does not have enough information to run an Accuforce wheel in FFB Foundation mode through SimCommander. 
It uses a dll provided by the user Motion4All on RaceDepartment.

### Setup

1. Extract the contents of the "WRCInjection.zip" file in the WRC subfolder of SpaceMonkey into your WRC 7/8/9 game folder.
2. Run the Install.bat file.

### Usage

1. Go to the main interface of Space Monkey and select a main config for WRC.
2. Go to the main interface of Space Monkey and press the WRC 7/8/9 button.
3. Press the Initialize! button.
4. Space Monkey will now wait for a connection from WRC and output telemetry automatically. You can launch WRC and any other software at this point.

---
## Richard Burns Rally (NGP 6)

### Setup

1. Ensure you have NGP 6 installed in your Richard Burns Rally installation.
2. Edit the RichardBurnsRally.ini file next to the RichardBurnsRally_SSE.exe and ensure that these settings under the [NGP] section look like this:

udpTelemetry=1

udpTelemetryAddress=192.168.50.194

udpTelemetryPort=6775

You may be able to use 127.0.0.1 for the udpTelemetryAddress

3. In the game make sure that options/plugins/ngp6/udp telemetry is turned on (u to toggle), but it should be if the RichardBurnsRally.ini is setup correctly.

### Usage

1. Go to the main interface of Space Monkey and select a main config for Richard Burns Rally.
2. Go to the main interface of Space Monkey and press the Richard Burns Rally button.
3. Specify the UDP receive port specified in the setup step (Default 6775)
4. Press the Initialize! button.
5. Space Monkey will now wait for a connection from Richard Burns Rally and output telemetry automatically. You can launch Richard Burns Rally and any other software at this point.

---
## STAR WARS: Squadrons

### Warning

This only works offline and with the Steam version of the game. You must uninstall EasyAntiCheat for Space Monkey to work. You need to block connections to the game in your firewall so that it can't tell the servers that you are playing with EasyAntiCheat disabled. Follow the Setup steps.

### Setup

1. Setup firewall rules to block udp and tcp from both the starwarssquadrons.exe and starwarssquadrons_launcher.exe files.
2. In the STAR WARS: Squadrons game folder there is a subfolder named EasyAntiCheat. Run EasyAntiCheat_Setup.exe and choose uninstall.
3. In the SpaceMonkey install folder there is a subfolder name Squadrons. Copy the steam_appid.txt from this folder into the STAR WARS: Squadrons game folder.

### Usage

1. Launch STAR WARS: Squadrons by running the starwarssquadrons.exe located in the game install folder.
2. Go to the main interface of Space Monkey and select a main config for Squadrons.
3. Go to the main interface of Space Monkey and press the STAR WARS: Squadrons button which will load the Squadrons UI.
4. Press the Initialize! button.
5. You can now switch back to STAR WARS: Squadrons and you should have telemetry once you start a game.

---

## Warplanes WW1

### Usage

1. Load the game.
2. Go to the main interface of Space Monkey and select a main config for Warplanes WW1..
3. Go to the main interface of Space Monkey and press the Warplanes WW1 button which will load the Warplanes WW1 UI.
4. In the Warplanes WW1 UI, click the Initialize button .
5. Space Monkey will now be outputting telemetry. Load any other software at this point.

---


## VTOL VR

### Usage

1. Load the game.
2. Go to the main interface of Space Monkey and select a main config for VTOL VR..
3. Go to the main interface of Space Monkey and press the VTOL VR button which will load the VTOL VR UI.
4. In the VTOL VR UI, click the Initialize button .
5. Space Monkey will now be outputting telemetry. Load any other software at this point.

---

## IL-2 Sturmovik

### Setup

1. Edit the file data/startup.cfg located within the IL-2 Sturmovik game folder and add the following:

[KEY = motiondevice]

addr = "127.0.0.1"

decimation = 1

enable = true

port = 4321

[END]

Simulation produces 50Hz rate data output (output 50 samples per second) of in-game player body's state: orientation, rotation speed (spin) and acceleration (if game mission has user-controlled body). To reduce UDP messages output rate the above setup section contains an integer setting “decimation”: UDP_output_rate = Data_output_rate / decimation The default setup makes UDP output rate at the simulation's rate and is equal 50Hz.

Some people may find better results with "decimation = 2".

### Usage

1. Go to the main interface of Space Monkey and select a main config for IL-2 Sturmovik.
2. Go to the main interface of Space Monkey and press the IL-2 Sturmovik button.
3. Specify the UDP receive port specified in the setup step (Default 4321)
4. Press the Initialize! button.
5. Space Monkey will now wait for a connection from IL-2 Sturmovik and output telemetry automatically. You can launch IL-2 Sturmovik and any other software at this point.


---


## Overload.

### Usage

1. Load the game. (Tested with the steam version)
2. Go to the main interface of Space Monkey and select a main config for Overload..
3. Go to the main interface of Space Monkey and press the Overload button which will load the OverloadUI.
4. In the Overload UI, click the Initialize button and wait for a message box to appear in the top left corner of the game window stating that SpaceMonkey is injected.
5. Space Monkey will now be outputting telemetry. Load any other software at this point.

---
## WRC Generations

### Warning

WRC Generations telemetry is still WIP, the game outputs telemetry at a non deterministic rate and some of the parameters are giving incorrect values; because of this you should follow the instructions 100% for the best experience and
be aware that you may experience some glitches.

### Setup

1. In explorer, navigate to C:\Users\<USERNAME>\Documents\My Games\WRCG
2. Open UserSettings.cfg in a text editor
3. Find the following lines and edit to match. (TelemetryRate must be 60 to match the internal update rate of SpaceMonkey and the update rate of the game.)

WRC.Telemetry.TelemetryRate = 60;

WRC.Telemetry.TelemetryAdress = "127.0.0.1";

WRC.Telemetry.EnableTelemetry = true;

WRC.Telemetry.TelemetryPort = 20777;



4. Launch WRC Generations
5. Navigate to Options / Video
6. Turn on v-sync. (with this set to false the telemetry will be very noisy).
7. Set Physics simulation synchronisation to High. (with this setting set to low the telemetry will be very noisy).
8. Close WRC Generations before proceeding to the Usage steps.



### Usage

1. Go to the main interface of Space Monkey and select a main config for WRC Generations.
2. Go to the main interface of Space Monkey and press the WRC Generations button.
3. Press the Initialize! button.
4. Space Monkey will now wait for a connection from WRC Generations and output telemetry automatically. You can launch WRC Generations and any other software at this point.

---
## Trail Out (deprecated use UEVR)

### Setup

1. Navigate to the TrailOut sub folder inside the Space Monkey install folder.
2. Extract the contents of TrailOut_0.3.zip into the game installation, there will be a folder named TrailOut containing two folders named Binaries and Content.


### Usage

1. Go to the main interface of Space Monkey and select a main config for Open Motion.
2. Go to the main interface of Space Monkey and press the Open Motion button.
3. Press the Initialize! button.
4. Space Monkey will now wait for a connection from Open Motion and output telemetry automatically. 
5. Navigate to the UnrealModLoader_V2.2.1 sub fodler inside the Space Monkey install folder.
6. Launch UnrealEngineModLauncher.exe
7. Launch Trail Out

---
## Mech Warrior 5 Mercenaries (deprecated use UEVR)

### Setup

1. Navigate to the MW5 sub folder inside the Space Monkey install folder.
2. Extract the contents of MW5Mercs_0.3.zip into the game installation, there will be a folder named MW5Mercs containing two folders named Binaries and Content.


### Usage

1. Go to the main interface of Space Monkey and select a main config for Open Motion.
2. Go to the main interface of Space Monkey and press the Open Motion button.
3. Press the Initialize! button.
4. Space Monkey will now wait for a connection from Open Motion and output telemetry automatically. 
5. Navigate to the UnrealModLoader_V2.2.1 sub fodler inside the Space Monkey install folder.
6. Launch UnrealEngineModLauncher.exe
7. Launch MW5

---
## Dakar Desert Rally (deprecated use UEVR)

### Setup

1. Navigate to the Dakar2 sub folder inside the Space Monkey install folder.
2. Extract the contents of Dakar2Mod_0.2.zip into the Dakar2Game subfolder of the game installation, there will be two folders named Binaries and Content.


### Usage

1. Go to the main interface of Space Monkey and select a main config for Open Motion.
2. Go to the main interface of Space Monkey and press the Open Motion button.
3. Press the Initialize! button.
4. Space Monkey will now wait for a connection from Open Motion and output telemetry automatically. 
5. Navigate to the UnrealModLoader_V2.2.1 sub fodler inside the Space Monkey install folder.
6. Launch UnrealEngineModLauncher.exe
7. Launch Dakar Desert Rally

---

## Tiny Combat Arena

### Usage

1. Load the game.
2. Go to the main interface of Space Monkey and select a main config for Tiny Combat Arena..
3. Go to the main interface of Space Monkey and press the Tiny Combat Arena button which will load the Tiny Combat Arena UI.
4. In the Tiny Combat Arena UI, click the Initialize button and wait for a message box to appear in the top left corner of the game window stating that SpaceMonkey is injected.
5. Space Monkey will now be outputting telemetry. Load any other software at this point.

---

## UEVR https://github.com/praydog/UEVR  

**The list of UEVR supported games is available on the [Flat to VR Modding Discord](https://discord.gg/Zr9qXePX) under the Unreal Engine VR section, in the ue-games channel**

### Setup for each game (needed once, or potentially at every new release)

1. Inject UEVR at least once into the game you want to play so UEVR creates a user data folder for the game. (A nightly build is included with SpaceMonkey in the UEVRRelease folder, for newer builds of UEVR get one directly from the UEVR github).
2. Stop the game and UEVR.
3. Launch Space Monkey.
4. Go to the main interface of Space Monkey and press the UEVR button.
5. In the UEVRUI that loads, select the name of the game you want to install SpaceMonkeyUEVR for in the combo box.
6. In the UEVRUI click the Install button. This will overwrite any existing SpaceMonkeyUEVR profile you have in your user data folder for the game; if you want to keep what you have in user data make a backup of the plugins/sm_game_config.json file.


### Usage (needed every time you want motion from UEVR)

1. Go to the main interface of Space Monkey and select a main config for UEVR.
2. Go to the main interface of Space Monkey and press the UEVR button.
3. In the SMTUI Press the Initialize! button.
4. Space Monkey will now wait for a connection from UEVR and output telemetry automatically. 
5. Run the game.
6. Launch UEVR and inject.
7. The output in UEVRUI should populate when you are recieving telemetry while in gameplay.


### Configuration (sm_game_config.json)

- For any new profiles or to request profile changes please post in the SpaceMonkey Discord. 
- These live in the SpaceMonkeyUEVR\UnrealVRMod folder and are copied into your user folder when installing through UEVRUI.
- They are json formatted files so editing them in a json editor that can tell you when there is errors in the formatting is preferred.
- If no profile exists for a game, installing will copy the default profile from the SpaceMonkeyUEVR\DefaultProfile folder. You can use the default profile or any of the other profiles as a starting point for a new game.

### Configuration Fields
- "m_plugin_type":"GPSimple" **This specifies the type of SpaceMonkeyUEVR plugin to use to generate motion, currently this should always be "GPSimple".**
- "m_pawn_display_name_substring":"DerivedMech_C" **This specifies a substring to match against the pawn name in the case where you want to ensure that you only recieve motion from a pawn who's name that contains this substring. (for example on the main menu). Leave this as an empty string "" to get any pawn.**
- "m_use_doubles":true **This tells SpaceMonkeyUEVR to expect double precision floats for transformations. Double precision was on by default in version 5.0 and up however it's still possible to use single precision in the engine, so this flag is required.**
- "m_object_path":[
	"Components",
	"ChildActorComponent",
	"Properties",
	"ChildActor",
	"Components",
	"Pilot_ChildActor",
	"Properties",
	"ChildActor"
	] **This is the path to an object which is a child of the pawn. This example is from MW Mercs and is used to find the pilot actor so that motion comes from the pilot transform and not just the pawn. You can figure this out in UEVR by turning on advanced settings and walking the tree of objects under the AcknowledgedPawn in the UObjectHook settings. Supports actors and sceneobjects at the bottom of the tree. Supports 'Components' and 'Properties' similar to UEVR UObjectHook.**
	  **The way this reads from bottom to top is: ChildActor is a Property of Pilot_ChildActor, which is a Component of ChildActor, which is a Property of ChildActorComponent, which is a Component of the Pawn**
- "m_transform_offset":{
		"m_locationX":0.0,
		"m_locationY":0.0,
		"m_locationZ":0.0,
		"m_rotationPitch": 0.0,
		"m_rotationYaw": -90.0,
		"m_rotationRoll": 0.0
	} **This is a transform offset applied in local space of the final transform to offset rotations/translation of the transform. m_locationX/Y/Z is in centimetres, m_rotationPitch/Yaw/Roll in degrees. In this example the pilot actor in MW Mercs is attached at a 90 degree rotation, so that needs to be corrected otherwise pitch and roll are swapped. This can also be used to do things like offsetting the transform to the position the player is in the vehicle so that motion is felt from the pilot's seat and not just the centre of rotation of the vehicle.**
- "m_tick_on_present":true **This is for if you want to tick in sync with the game's render thread instead of the game's update thread for whatever reason, usually just leave this to false or omit it from the file as motion performance is worse in this mode.**

### Running UEVR without VR

- In your UEVR release folder rename openvr_api.dll and openxr_loader.dll to something else. This prevents VR from starting, but only if the game doesn't already support VR.
- Inject UEVR; ignore the warning that openvr_api.dll is missing.
- Under VR/Debug options in the UEVR ingame UI tick "Stereo Emulation Mode".

---

# Sim Racing Studio

More info here

https://www.simracingstudio.com/post/do-you-play-wreckfest-dirt-5-wrc-nascar-4---5-star-wars-squadron-vtol-vr-www1-etc

---

# SimCommander 4

### Setup
1. Create a new game entry under settings with the following settings. Point the Game Exe at the SpaceMonkeyTP.exe in the location you installed it to previously.
![SC4Game](https://github.com/PHARTGAMES/SpaceMonkey/blob/main/Documentation/SC4Game.PNG?raw=true))]

2. For car games, you have the option to create a duplicate of an existing Dirt Rally 2.0 or Dirt 4 profile, for Aircraft games you can duplicate an X-Plane profile. You can also create a profile from scratch, then change it's settings as follows.
![SC4Profile](https://github.com/PHARTGAMES/SpaceMonkey/blob/main/Documentation/SC4Profile.PNG?raw=true))]

### Usage

1. Click the launch button on your new profile, SpaceMonkey will load.
2. Perform the Usage steps for the game you wish to use, as described in this document.


---

# SimFeedback

Setup instructions here

https://github.com/PHARTGAMES/SpaceMonkey/blob/main/GTPSimfeedback/README.md

---

# MMF Support

The mutex used by SpaceMonkey is named "GenericTelemetryProviderMutex"

The MMF used by SpaceMonkey is named "GenericTelemetryProviderFiltered"

Example MMF usage here https://github.com/PHARTGAMES/SpaceMonkey/blob/main/GTPSimfeedback/GTPTelemetryProvider.cs

---

# Callback Interface

Actual example here https://github.com/PHARTGAMES/SpaceMonkey/blob/main/GTPSimfeedback/GTPTelemetryProvider.cs

Simplified example
```cs
using GenericTelemetryProvider;
using CMCustomUDP;

public void TelemetryCallback(CMCustomUDPData telemetryData)
{
	//use telemetryData here
}

public void Init()
{

	AppDomain currentDomain = AppDomain.CurrentDomain;

	AppDomain.CurrentDomain.AssemblyResolve += (object sender, ResolveEventArgs args) =>
	{
		try
		{
			string assemblyName = args.Name.Split(',')[0];

			RegistryKey localKey;
            if (Environment.Is64BitOperatingSystem)
                localKey = RegistryKey.OpenBaseKey(RegistryHive.LocalMachine, RegistryView.Registry64);
            else
                localKey = RegistryKey.OpenBaseKey(RegistryHive.LocalMachine, RegistryView.Registry32);

            string installPath = localKey.OpenSubKey("SOFTWARE\\PHARTGAMES\\SpaceMonkeyTP").GetValue("install_path").ToString();
			if (string.IsNullOrEmpty(installPath))
			{
				throw new Exception("SpaceMonkey Not Installed");
			}
			else
			{
				Assembly ass = Assembly.LoadFrom(installPath + assemblyName + ".dll");

				return ass;
			}
		}
		catch (Exception e)
		{
			Console.WriteLine("Failed to load assembly: " + e.Message);
			return null;
		}
	};

	SMClient.Init((success) => //this will load the SpaceMonkey window
	{	
		SMClient.RegisterTelemetryCallback(TelemetryCallback); //this will register the callback
	);
}
```
---

# ChangeLog

Release v1.0.5

1. Added Overload support
2. Added Extra telemetry for engine, gears and suspension to BeamNG.drive. This will work with SimCommander Simvibe.
3. Added Wreckfest Experimental for SRS users.
4. Fixes for crashes caused by incorrect culture being set.
5. Fixes for timer accuracy.
6. Fixes for app not closing threads correctly at shutdown.


Release v1.0.6

1. Added WRC Generations support
2. Added Trail Out support
3. Added MechWarrior 5 Mercenaries support
4. Added Dakar Desert Rally support
5. Added Tiny Combat Arena support
6. Wreckfest telemetry improvements (fixed noise, 64bit support)
7. GTAV updated to support latest scripthook.net
8. General rework and cleanup to start moving providers toward Open Motion.


Release v1.0.7

1. Added Codemasters extradata=3 support to allow output to more apps that don't support custom_udp such as SimHub.
2. Added multiple output configuration support through the Outputs Interface.
3. OpenMotion api expanded to support engine and gear telemetry as well as math rewrite.
4. Added telemetry callback interface and restructured project to be loaded as a dll.
5. Simfeedback plugin gets SpaceMonkey integration and callback support.


Release v1.0.8

1. Added EA Sports WRC Support


Release v1.0.9

1. Try fix dependency issues in GTPSimfeedback and SpaceMonkeyTP
2. Fix EA WRC axis issues.


Release v1.1.0

1. Fixed issues reading install folder from registry in GTPSimfeedback and SpaceMonkeyTP
2. Add EAWRC profile to GTPSimfeedback


Release v1.1.1

1. Add slip_angle and slip_angle2 to output; use defaultPacketFormat_SlipAngle when outputting mmf or udp if you would like to use these values.
2. Fix race conditions in WRC and BeamNG that started to break with "2023-11 Cumulative Update for .NET Framework 3.5, 4.8 and 4.8.1 for Windows 10 Version 22H2 for x64 (KB5032339)"


Release v1.2.0

1. Add UEVR support.
2. Update VTOL VR.
3. Add Wreckfest 2 support.


Release v1.2.1

1. 50x faster scan in Wreckfest and Wreckfest 2


Release v1.2.2

1. Fix Monster Games telemetry not working. (Nascar heat 5 etc)

---


# Known Issues

https://github.com/PHARTGAMES/SpaceMonkey/issues

---

# Support

Enter an issue here https://github.com/PHARTGAMES/SpaceMonkey/issues


 [Discord](https://discord.gg/gGUufTdpgG)

---

# Support Me

- [Patreon](https://patreon.com/PHARTGAMES)

# Contributors

---

https://github.com/PHARTGAMES/SpaceMonkey/graphs/contributors

---

# Special Thanks

Tiger Feet oO0o for helping me debug registry issues in production; you're awesome!


