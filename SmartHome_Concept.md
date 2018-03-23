# Items

|id|Item Name | Description | Command Types |
|:--|:-----------|:--------------|:------------|
|1|**Color**		| Color information (RGB)						|	OnOff, IncreaseDecrease, Percent, HSB|
|2|**Contact**	| Item storing status of e.g. door/window contacts	| OpenClose |
|3|**DateTime**	|Stores date and time	| - |
|4|**Dimmer **	|Item carrying a percentage value for dimmers |	OnOff, IncreaseDecrease, Percent |
|5|**Group** | Item to nest other items / collect them in groups	| - |
|6|**Image**	| Holds the binary data of an image|	-  |
|7|**Location** |Stores GPS coordinates	| Point |
|8|**Number** | Stores values in number format, takes an optional dimension suffix | Decimal |
|9|**Number:**| like Number, additional dimension information for unit support | Quantity |
|10|**Player**| Allows to control players (e.g. audio players)| PlayPause, NextPrevious, RewindFastforward |
|11|**Rollershutter** | Typically used for blinds |	UpDown, StopMove, Percent |
|12|**String**| Stores texts	| String |
|13|**Switch**	| Typically used for lights (on/off) | OnOff |


## Group functions
|id|Function	|Parameters	|Base Item	|Description|
|:--|:-----------|:--------------|:------------|:---------|
|1|**EQUALITY**|-	| all	|Sets the state of the members if all have equal state. Otherwise UNDEF is set.|
|2|**AND, OR, NAND, NOR**|	,|	all (must match active & passive state)	|Sets the <activeState>, if the member state <activeState> evaluates to true under the boolean term. Otherwise the <passiveState> is set.|
|3|**SUM, AVG, MIN, MAX**|	-	| Number	|Sets the state according to the arithmetic function over all member states.|
|4|**COUNT**|	| Number |	Sets the state to the number of members matching the given regular expression with their states.|

### Examples for derived states on group items when declared in the item DSL

* Group:Number:COUNT(".*") counts all members of the group matching the given regular expression, here any character or state (simply count all members).
* Group:Number:AVG calculates the average value over all member states which can be interpreted as DecimalTypes.
* Group:Switch:OR(ON,OFF) sets the group state to ON if any of its members has the state ON, OFF if all are off.
* Group:Switch:AND(ON,OFF) sets the group state to ON if all of its members have the state ON, OFF if any of the group members has a different state than ON



#Things


## Thing Status
|id|Status	|Description|
|:---|:----------|:----------|
|1|**UNINITIALIZED**	|This is the initial status of a thing, when it is added or the framework is being started. This status is also assigned, if the initializing process failed or the binding is not available. Commands, which are sent to channels will not be processed.|
|2|**INITIALIZING**	|This state is assigned while the binding initializes the thing. It depends on the binding how long the initializing process takes. Commands, which are sent to channels will not be processed.|
|3|**UNKNOWN**|The handler is fully initialized but due to the nature of the represented device/service it cannot really tell yet whether the thing is ONLINE or OFFLINE. Therefore the thing potentially might be working correctly already and may or may not process commands. But the framework is allowed to send commands, because some radio-based devices may go ONLINE if a command is sent to them. The handler should take care to switch the thing to ONLINE or OFFLINE as soon as possible.|
|4|**ONLINE**	|The device/service represented by a thing is assumed to be working correctly and can process commands.|
|5|**OFFLINE**|The device/service represented by a thing is assumed to be not working correctly and may not process commands. But the framework is allowed to send commands, because some radio-based devices may go back to ONLINE, if a command is sent to them.|
|6|**GONE** |	The device has been removed from the bridge or the network to which it belongs and is no longer available for use. The user can now remove the thing from the system.|
|7|**REMOVING** |	The device/service represented by a thing should be removed, but the binding did not confirm the deletion yet. Some bindings need to communicate with the device to unpair it from the system. Thing is probably not working and commands can not be processed.|
|8|**REMOVED**|This status indicates that the device/service represented by a thing was removed from the external system after the REMOVING was initiated by the framework. Usually this status is an intermediate status because the thing gets removed from the database after this status was assigned.|


## Thing Categories

|id|Category|	Description	|Icon Example|
|:---|:-----|:--------|:----------|
|1|Battery|	Batteries, Energy Storages	|battery.png|
|2|Blinds|	Roller shutters, window blinds, etc.|	blinds.png|
|3|Camera|	All kinds of cameras	|camera.png|
|4|Car|	Smart Cars	|   |
|5|CleaningRobot|	Vacuum robots, mopping robots, etc.|   |	
|6|Door	| Door	| door.png |
|7|FrontDoor	|Front Door	| frontdoor.png|
|8|GarageDoor	|Garage Door	|garagedoor.png|
|9|HVAC |	Air condition devices, Fans	|   |
|10|Inverter |Power inverter, such as solar inverters etc. | |	
|11|LawnMower |Lawn mowing robots, etc.|lawnmower.png|
|12|Lightbulb | Devices that illuminate something, such as bulbs, etc.	| lightbulb.png |
|13|Lock |Devices whose primary pupose is locking something| lock.png |
|14|MotionDetector | Motion sensors/detectors |  |	
|15|NetworkAppliance |Bridges/Gateway need to access other devices like used by Philips Hue for example, Routers, Switches	|
|16|PowerOutlet| Small devices to be plugged into a power socket in a wall which stick there | poweroutlet.png |
|17|Projector|Devices that project a picture somewhere |	projector.png |
|18|RadiatorControl| Controls on radiators used to heat up rooms|   |
|19|Receiver|Audio/Video receivers, i.e. radio receivers, satelite or cable receivers, recorders, etc.|receiver.png|
|20|RemoteControl|	Any portable or hand-held device that controls the status of something, e.g. remote control, keyfob etc.||
|21|Screen	|Devices that are able to show a picture|	screen.png|
|22|Sensor|	Device used to measure something |    |	
|23|Siren| 	Siren used by Alarm systems	|siren.png|
|24|SmokeDetector| 	Smoke detectors	|    |
|25|Speaker	|Devices that are able to play sounds	|    |
|26|WallSwitch	|Any device attached to the wall that controls the status of something, for ex. a light switch, dimmer	|wallswitch.png|
|27|WebService	| Account with credentials for a website|    |
|28|Window	| Window| window.png |
|29|WhiteGood	|Devices that look like Waschingmachines, Dishwashers, Dryers, Fridges, Ovens, etc|    |


## Channel Categories

### Widgets
|id |Category|Icon Example|
|:------|:------|:------|
|1| Colorpicker	| colorpicker |
|2| Number	| number |
|3|Rollershutter|rollershutter|
|4|Slider|	slider|
|5|Switch|	switch|
|6|Text|	text|
|7|Group|	group|

### Weather
|id|Category|	Icon Example|
|:---|:-----|:----------|
|1|Sun|	sun|
|2|Moon|moon|
|3|Clouds|clouds|
|4|Sun_Clouds|sun_clouds|
|5|Rain|rain|
|6|Snow|snow|
|7|Wind|wind|
|8|Humidity|humidity|
|9|Temperature|	temperature|

### Properties
|id|Category|Icon Example|
|:----|:-----|:-------|
|1|BatteryLevel|batterylevel|
|2|LowBattery|lowbattery|
|3|CarbonDioxide|carbondioxide|
|4|Energy|energy|
|5|Gas|gas|
|6|Oil|oil|
|7|Water|water|
|8|Light|light|
|9|ColorLight|colorlight|
|10|Temperature|temperature|
|11|Smoke|smoke|
|12|SoundVolume|soundvolume|
|13|Pressure|pressure|
|14|Fire|	fire|
|15|Motion	|motion|
|16|QualityOfService|	qualityofservice|
|17|Moisture|moisture|
|18|Noise|	noise|
|19|Flow|flow|
|20|Price|	price|
|21|Time|time|

### Control
|id|Category|Icon Example|
|:---|:---|:---|
|1|Heating|heating|
|2|MediaControl|mediacontrol|
|3|MoveControl|movecontrol|
|4|Zoom| |

### Purpose
|id| Category|Icon Example|
|:----|:----|:----|
|1|Alarm|alarm|
|2|Presence|presence|
|3|Vacation|vacation|
|4|Party|party|
