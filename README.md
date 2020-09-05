
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
Create a folder with the in this kind of pattern "[yourname]-livery-[aircraft-type]-[liveryname]"
For Example: "revyn112-livery-a32n-easyjet-berlin".

Nice to know: This is the pattern-rule of Asobo for 3rd parties / content creators in the sdk documentation.

##### 2. Inside the folder create the followering structure [or download the template below]
    .
    +-- layouts.json
    +-- manifest.json
    +-- SimObjects
    |   +-- AirPlanes
    |   |   +-- [CREATOR_AIRCRAFT_TYPE]
    |   |   +-- aircraft.cfg
    |   |   |   +-- TEXTURE.[YOUR_LIVERY_NAME]

##### 3. Add your texture files
Add your texture files like before into the folder

    "SimObjects/Airplanes/[CREATOR_AIRCRAFT_TYPE]/TEXTURE.[YOUR_LIVERY_NAME]"`

##### 4. Setup the aircraft.cfg

    [VERSION]
    major = 1
    minor = 0
    
    [VARIATION]
    base_container = "..\Asobo_A320_NEO"
    
    ;===================== FLTSIM =====================
    [FLTSIM.0]
    title = "Airbus A320 Neo Custom"  ; Variation name
    model = ""  ; model folder
    panel = ""  ; panel folder
    sound = ""  ; sound folder
    texture = "CUSTOM"  ; texture folder
    kb_checklists = "Boeing747-400_check"  ; Procedures/Checklist sibling file name
    kb_reference = "Boeing747-400_ref"  ; Reference information sibling file name
    description = "TT:AIRCRAFT.DESCRIPTION"  ; Variation description.
    wip_indicator = 0 ; know if the variation is good to go or still WIP : -1=Disabled, 0=Rough, 1=1st Pass, 2=Finished
    ui_manufacturer = "TT:AIRCRAFT.UI_MANUFACTURER"  ; e.g. Boeing, Cessna
    ui_type = "A320neo Custom"  ; e.g. 747-400, 172
    ui_variation = "Berlin"  ; e.g. World Air, IFR Panel
    ui_typerole = "Commercial Airliner"  ; e.g. Single Engine Prop, Twin Engine Prop, motorcraft, etc
    ui_createdby = "Revyn112"  ; e.g. Asobo Studio, Microsoft, FSAddonCompany, etc
    ui_thumbnailfile = ""  ; app relative path to ThumbNail image file
    ui_certified_ceiling = 39800 ; service ceiling / max certified operating altitude (ft)
    ui_max_range = 3500 ; max distance the aircraft can fly between take-off and landing in (NM)
    ui_autonomy = 7 ; max duration the aircraft can fly between take-off and landing in (Hrs)
    ui_fuel_burn_rate = 5300 ; average fuel consumption per hour (lbs/hr) - reminder: fuel density is ~6.7lbs per US gallon
    atc_id = "OE-IZQ"  ; tail number
    atc_id_enable = 1 ; enable tail number
    atc_airline = "Airline"  ; airline name
    icao_airline = "CUS"  ; airline icao code
    atc_flight_number = ""  ; flight number
    atc_heavy = 1 ; heavy?
    atc_parking_types = "GATE,RAMP,CARGO"  ; "ANY" / "RAMP" / "CARGO" / "MIL_CARGO" / "MIL_COMBAT" / "GATE" / "DOCK"
    atc_parking_codes = ""  ; Comma separated and may be as small as one character each
    atc_id_color = ""  ; color for the tail number : i.e. "#ffff00ff"
    atc_id_font = ""  ; font for the tail number
    isAirTraffic = 0 ; Is the plane usable for air traffic
    isUserSelectable = 1 ; Is the plane selectable by the user    

##### 5. Setup the manifest.json
Copy this content into the manifest.json

    {
	    "dependencies": [],
	    "content_type": "AIRCRAFT",
	    "title": "Your Package Name",
	    "manufacturer": "Airbus",
	    "creator": "Revyn112",
	    "package_version": "0.1.0",
	    "minimum_game_version": "1.7.12",
	    "release_notes": {
		    "neutral": {
			    "LastUpdate": "",
			    "OlderHistory": ""
		    }
	    }
    }

##### 6. Setup the layouts.json
To create a layouts.json file you can use the JSON Tool of @S3RI0US. 
Explanation and download you will find here: https://forums.flightsimulator.com/t/tool-mfs-2020-auto-json-for-layout-json/245505

##### 7. You are ready for takeoff!

That's all - now you have to pack the files into a .zip archive and distribute them on the forum or on the countless hosting sites. The user just have to unpack your archive and drag'n'drop the packages into the community folder.
Simple... Isn't It?

### Credits
Originally found by OzWookiee @ fsdeveloper.com
