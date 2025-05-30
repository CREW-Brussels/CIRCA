# CIRCA
CIRCA (Crew InteRaCtive Archive) is an implementation for Unreal Engine aimed at recording Location Based experiences and performances (LBX) into Unreal, baking them into a standalone application for playback with or without VR headset.

***
Requirements:
- Unreal Engine 5.3
- [Download](https://github.com/CREW-Brussels/CIRCA.git) the plugin's folder in the Plugins folder of your project here or if your project is on git, add this command in the Plugins folder of your project:
```
git add submodule https://github.com/CREW-Brussels/CIRCA.git
```
***

CIRCA (Crew InteRaCtive Archive) is an implementation for Unreal Engine aimed at recording Location Based experiences and performances (LBX) into Unreal, baking them into a standalone application for playback with or without VR headset.

CIRCA is currently in active development, in particular regarding the UI/UX to replay in VR.

![CIRCA_GIF_vf](https://github.com/user-attachments/assets/fa80f8b4-c44d-4c81-8e56-f733eb23fecf)

***
# How to use CIRCA in a project?

### REQUIREMENTS

* Unreal Engine 5.3
* Download CIRCA Plugin (Link coming) and install it to your project's PlugIn folders.
* Make sure it's actvated in the Plugin's menu.

***

### RECORD

In your scene that will be recorded:

1. Change the Game Mode Class of your scene in World Overridde

3. Change it to **BP_CIRCA_Record_GameMode**
-> In UE, the Game Mode acts as the blueprint for the overall gameplay logic, determining aspects such as player characters. Here, changing the Gamemode to the **BP_CIRCA_Record_GameMode** will allow us to use CIRCA's recording tools.

![Screenshot 2025-04-02 154344](https://github.com/user-attachments/assets/bd06c6b0-39e0-413e-bdb1-a2f8e3a33f5a)

***
> Additional note: If you are using VR, and our CREW XR Template (link coming), you should follow the next steps. It allows using VR Players, at the same time as using settings to record our performance with CIRCA.
> * Create a new Game Mode in World Overridde, inherited from GameModeBase
> * Edit it 
> * Go to: File > Reparent Blueprint > **BP_CIRCA_Record_GameMode**
> * Player State Class: BP_XR_PlayerState

> ![GameMode_CIRCA_XR-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/e833ea54-4140-4be9-9e6e-984cd542db92)

> * Default Pawn Class: create new blueprint class pawn, reparented from BP_XR_Player. Here we're naming it BP_XR_CIRCA_Player.

> ![BP_CIRCA_XR_Player-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/0abe4c9a-1a06-4fb5-92d3-dba6841c0a82)
***

3. Change Net Mode as: **Play as listen server**

![Screenshot 2025-04-02 161911](https://github.com/user-attachments/assets/1dc533b8-5fb3-448e-8660-97cfebdc8a94)

4. For **every movable element that needs to be recorded**: 

Edit them, and add the component **CIRCA_Recorded**

![Screenshot 2025-04-02 164031](https://github.com/user-attachments/assets/0388d8a7-0d3c-494b-91ea-b2b2a7a89aed)

> In the case you have a VR Player, also add the component in BP_XR_CIRCA_Player created earlier.

5. Use key R to Record the scene and E to End the Recording in the editor of the server, while the level is being played.

***

### REPLAY

Perform the following steps after having made a recording: 

1. Duplicate the level and open it. We will use this second level to replay the recordings.

2. Change the Game Mode World Overridde, to **BP_CIRCA_Replay_GameMode**

3. Open the Sequencer and drop the scene Level Sequence in the scene. You should find the Level Sequence asset of your recording in Cinematics > Takes > Date > Scene_1_01

4. Drag and drop it in your scene

**In details -> add Tag: CIRCA**
![Screenshot 2025-05-19 163801](https://github.com/user-attachments/assets/c86b4598-94ce-4290-b26d-31715f9ed297)

![Screenshot 2025-04-03 121817](https://github.com/user-attachments/assets/2e82098c-a103-4028-9920-a51072f6ee17)

5. For every XR player recorded you should:
- open the recording of the level
- double click on the sequencer of the player
- mute the last transform (see screenshot)

![CIRCA-VRPLAYER-MUTE](https://github.com/user-attachments/assets/d98f4fec-a6dc-44b4-9026-e89c11f2e7bc)

***

### Package the project into an app

1. In Editor -> Project Settings -> Maps & Modes

Change the default map to the CIRCA Player map you last created:

![Screenshot 2025-04-03 144807](https://github.com/user-attachments/assets/d457f21d-d68a-4c7c-a5ba-ba54228d6e7f)

2. Package your project for Windows, no additional settings have to be modified

![Screenshot 2025-04-03 145005](https://github.com/user-attachments/assets/2c2b650d-ba8e-4e7f-8604-4999b0c7fc53)

-> You should now have a working app. If it was a multiplayer experience, it is also possible

***

## About
<img src="https://github.com/user-attachments/assets/2ffa225b-2966-4f68-8106-3fd403fd6988" alt="CREW-LOGO" width="130"/>  
<img src="https://emil-xr.eu/wp-content/uploads/2022/10/logo_emil-272x300.png)" alt="EMIL-XR-LOGO" width="100"/>

> CIRCA, a submodule of EXP, is being developed by [CREW](http://crew.brussels) as part of [EMIL](https://emil-xr.eu/), the European Media and Immersion Lab, an Innovation Action funded by the European Union and co-funded by Innovate UK. 

## Funding
<img src="https://emil-xr.eu/wp-content/uploads/2022/10/EN-Funded-by-the-EU-POS-1024x215.png)" alt="EU" height="100"/>

> This project has received funding from the European Union's Horizon Europe Research and Innovation Programme under Grant Agreement No 101070533 EMIL.
