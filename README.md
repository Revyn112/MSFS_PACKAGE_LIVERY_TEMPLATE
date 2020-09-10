
## [HOW-TO / GUIDE] Creating User-Friendly Livery Packages

### Some words before
This guide doesn't explain how to make a livery of your favourit plane for MSFS.
This guide should explain livery creator how you should made your livery packages "user-friendly".


### The current problem of liveries
The way of adding new liveries for a aircraft results into the user have to edit the aircraft.cfg, adds a block of code for the new livery, has to adjust the fltsim.X number and have to edit the layout.json to add all the new files.
All-in-all this method is not really user-friendly.


### We can do it make easier for all!

But how? The easiest way for all user is, just to drag'n'drop the livery-package into the community directory.
No edit, no adjustment, happy user, happy flying.


### And so it is done!
#### Setup your livery-package


##### 1. Setup the package
Create a folder with the in this kind of pattern "[yourname]-livery-[aircraft-icao-type]-[liveryname]"

In this guide i used the former german airline "AIRBERLIN" and the ASOBO A320neo as example.


Example: 

    "revyn112-livery-a32n-airberlin-standard".


*Nice to know:* This is the pattern-rule of Asobo for 3rd parties / content creators in the sdk documentation.


##### 2. Inside the folder create the followering structure [or download the template below]
    .
    +-- layouts.json
    +-- manifest.json
    +-- SimObjects
    |   +-- AirPlanes
    |   |   +-- [CREATOR_AIRCRAFT_TYPE_LIVERY_NAME_CREATOR_NAME] (Make sure this name is globally unique)
    |   |   +-- aircraft.cfg
    |   |   |   +-- MODEL
    |   |   |   +-- MODEL.AI_[YOUR_LIVERY_NAME]
    |   |   |   +-- TEXTURE.[YOUR_LIVERY_NAME]
    

##### 3. Setup the files and add your texture files

Rename the folder `"ASOBO_A320_NEO_CUSTOM_NAME"` inside the folder `AirPlanes`. Be sure that the folder name is unique.

In my example:

    "ASOBO_A320_NEO_airberlin_Standard_Revyn112"

Add your custom texture files into the folder `TEXTURE.[YOUR_LIVERY_NAME]` and rename it.
Be sure to keep the `TEXTURE.` prefix. 

Example: 

    "TEXTURE.AIRBERLIN_STANDARD"


The final result should be this:
    
    "SimObjects/AirPlanes/ASOBO_A320_NEO_airberlin_Standard_Revyn112/TEXTURE.AIRBERLIN_STANDARD"


***Important: Don't change the texture.CGF in the TEXTURE folder.***


##### 4. Setup the AI Model

In this Guide we add also an AI-TRAFFIC model for better performance (low polycount model, no interior). The AI model defintions are in the block `FLTSIM.1`. You just have to rename `MODEL.AI_[YOUR_LIVERY_NAME]` to your livery name. No need for more configurations inside the folder and files.

Example:

    "MODEL.AI_AIRBERLIN_STANDARD"

Be sure that `FLTSIM.0` (for player aircraft) parameters in `aircraft.cfg` are:
    
    model = ""
    isAirTraffic: 0
    isUserSelectable = 1

Be sure that `FLTSIM.1` (for ai aircraft) parameters in `aircraft.cfg` are:
    
    model = "AI_AIRBERLIN_STANDARD"  ; (The name of the Folder "MODEL.AI_[YOUR_LIVERY_NAME])
    isAirTraffic: 1
    isUserSelectable = 0


If you don't want to use an seperate AI model remove both `model` folder and the `FLTSIM.1` defintion in the `aircraft.cfg`.


##### 5. Setup the aircraft.cfg

Adjust/Replace the followering parameters in `FLTSIM.0` and `FLTSIM.1` defintions:

    title: "Airbus A320 Neo airberlin Revyn112 [AI]"
    texture: "AIRBERLIN_STANDARD" (The name of the Folder "TEXTURE.[YOUR_LIVERY_NAME])
    ui_type: "A320neo airberlin Standard" (Title for the Ingame Texture Selection)
    ui_variation: "airberlin Standard" (Name of your custom Design)
    ui_createdby: "Revyn112" (Obviously your creator name)
    atc_id: "D-ABZI" (Choose a Standard tailnumber)
    atc_airline: "airberlin" (Name of the airline)
    icao_airline: "BER" (ICAO code of the airlin)

Template of the `aircraft.cfg`

    [VERSION]
    major = 1
    minor = 0
    
    [VARIATION]
    base_container = "..\Asobo_A320_NEO"
    
    ;===================== FLTSIM USER DEFINTION =====================
    [FLTSIM.0]
    title = "Airbus A320 Neo Custom"  ; Variation name
    model = ""  ; model folder
    panel = ""  ; panel folder
    sound = ""  ; sound folder
    texture = "[YOUR_LIVERY_NAME]"  ; texture folder
    kb_checklists = "Boeing747-400_check"  ; Procedures/Checklist sibling file name
    kb_reference = "Boeing747-400_ref"  ; Reference information sibling file name
    description = "TT:AIRCRAFT.DESCRIPTION"  ; Variation description.
    wip_indicator = 0 ; know if the variation is good to go or still WIP : -1=Disabled, 0=Rough, 1=1st Pass, 2=Finished
    ui_manufacturer = "TT:AIRCRAFT.UI_MANUFACTURER"  ; e.g. Boeing, Cessna
    ui_type = "A320neo Custom"  ; e.g. 747-400, 172
    ui_variation = "Custom"  ; e.g. World Air, IFR Panel
    ui_typerole = "Commercial Airliner"  ; e.g. Single Engine Prop, Twin Engine Prop, motorcraft, etc
    ui_createdby = "YOUR_NAME"  ; e.g. Asobo Studio, Microsoft, FSAddonCompany, etc
    ui_thumbnailfile = ""  ; app relative path to ThumbNail image file
    ui_certified_ceiling = 39800 ; service ceiling / max certified operating altitude (ft)
    ui_max_range = 3500 ; max distance the aircraft can fly between take-off and landing in (NM)
    ui_autonomy = 7 ; max duration the aircraft can fly between take-off and landing in (Hrs)
    ui_fuel_burn_rate = 5300 ; average fuel consumption per hour (lbs/hr) - reminder: fuel density is ~6.7lbs per US gallon
    atc_id = "T-TAIL"  ; tail number
    atc_id_enable = 1 ; enable tail number
    atc_airline = "YOUR AIRLINE NAME"  ; airline name
    atc_flight_number = ""  ; flight number
    atc_heavy = 1 ; heavy?
    atc_parking_types = "GATE,RAMP,CARGO"  ; "ANY" / "RAMP" / "CARGO" / "MIL_CARGO" / "MIL_COMBAT" / "GATE" / "DOCK"
    atc_parking_codes = ""  ; Comma separated and may be as small as one character each
    atc_id_color = ""  ; color for the tail number : i.e. "#ffff00ff"
    atc_id_font = ""  ; font for the tail number
    icao_airline = "CUS"  ; airline icao code
    isAirTraffic = 0 ; Is the plane usable for air traffic
    isUserSelectable = 1 ; Is the plane selectable by the user   
    
    ;===================== OPTIONAL FLTSIM AI DEFINTION =====================
    [FLTSIM.1]
    title = "Airbus A320 Neo Custom AI"  ; Variation name
    model = "AI_[YOUR_LIVERY_NAME]"  ; model folder
    panel = ""  ; panel folder
    sound = ""  ; sound folder
    texture = "[YOUR_LIVERY_NAME]"  ; texture folder
    kb_checklists = "Boeing747-400_check"  ; Procedures/Checklist sibling file name
    kb_reference = "Boeing747-400_ref"  ; Reference information sibling file name
    description = "TT:AIRCRAFT.DESCRIPTION"  ; Variation description.
    wip_indicator = 0 ; know if the variation is good to go or still WIP : -1=Disabled, 0=Rough, 1=1st Pass, 2=Finished
    ui_manufacturer = "TT:AIRCRAFT.UI_MANUFACTURER"  ; e.g. Boeing, Cessna
    ui_type = "A320neo Custom AI"  ; e.g. 747-400, 172
    ui_variation = "Custom"  ; e.g. World Air, IFR Panel
    ui_typerole = "Commercial Airliner"  ; e.g. Single Engine Prop, Twin Engine Prop, motorcraft, etc
    ui_createdby = "YOUR_NAME"  ; e.g. Asobo Studio, Microsoft, FSAddonCompany, etc
    ui_thumbnailfile = ""  ; app relative path to ThumbNail image file
    ui_certified_ceiling = 39800 ; service ceiling / max certified operating altitude (ft)
    ui_max_range = 3500 ; max distance the aircraft can fly between take-off and landing in (NM)
    ui_autonomy = 7 ; max duration the aircraft can fly between take-off and landing in (Hrs)
    ui_fuel_burn_rate = 5300 ; average fuel consumption per hour (lbs/hr) - reminder: fuel density is ~6.7lbs per US gallon
    atc_id = "T-TAIL"  ; tail number
    atc_id_enable = 1 ; enable tail number
    atc_airline = "YOUR AIRLINE NAME"  ; airline name
    atc_flight_number = ""  ; flight number
    atc_heavy = 1 ; heavy?
    atc_parking_types = "GATE,RAMP,CARGO"  ; "ANY" / "RAMP" / "CARGO" / "MIL_CARGO" / "MIL_COMBAT" / "GATE" / "DOCK"
    atc_parking_codes = ""  ; Comma separated and may be as small as one character each
    atc_id_color = ""  ; color for the tail number : i.e. "#ffff00ff"
    atc_id_font = ""  ; font for the tail number
    icao_airline = "CUS"  ; airline icao code
    isAirTraffic = 1 ; Is the plane usable for air traffic
    isUserSelectable = 0 ; Is the plane selectable by the user


##### 6. Setup the manifest.json

Adjust/Replace the parameters in the `manifest.json` inside the root folder.

    dependencies =>             Add package dependencies
    content_type =>             Should be "AIRCRAFT"
    title =>                    Your Package Title
    manufacturer =>             Aircraft manufacturer [airbus/boeing/bombardier...]
    creator =>                  Your name
    package_version =>          Your package Version
    minimum_game_version =>     The minimum game version your package will work
    release_notes =>            The Release notes for your package (can be empty)


In this example `manifest.json` will looks like this:

    {
        "dependencies": [
            {
            "name": "asobo-aircraft-a320-neo",
            "package_version": "0.1.51"
            }
        ],
        "content_type": "AIRCRAFT",
        "title": "A320neo airberlin Standard",
        "manufacturer": "Airbus",
        "creator": "Revyn112",
        "package_version": "1.0.0",
        "minimum_game_version": "1.7.12",
        "release_notes": {
            "neutral": {
            "LastUpdate": "",
            "OlderHistory": ""
            }
        }
    }


##### 7. Setup the layouts.json
To create a layouts.json file you should use the JSON Tool of @S3RI0US. 
You will find the explanation and download here: https://forums.flightsimulator.com/t/tool-mfs-2020-auto-json-for-layout-json/245505

**Be sure to create an layouts.json, without this file your package won't work properly**

##### 8. You are ready for takeoff!

That's all - now you have to pack the files into a .zip archive and distribute them on the forum or on the countless hosting sites. The user just have to unpack your archive and drag'n'drop the package into the community folder.
Simple... Isn't It?


### Credits
Drag'n'Drop method found by OzWookiee @ fsdeveloper.com
