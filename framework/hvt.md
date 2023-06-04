# HVT Task Module
## Description
This module adds support for HVT Capture or Eliminate Tasks/Missions.

The mission maker must define HVT units, the framework will monitor the status of those units.

An extraction area and a threshold must be set, specifying the given amount of HVTs that have to be in the extraction zone or eliminated in order to complete the task.

The module can also trigger mission complete or mission fail.

## Usage
### Setup HVT(s)
1. Setup the HVT Task scene
2. Place down the HVT unit(s)
3. Place down an area marker that marks the extraction zone, also give it a unique name
4. Call the `sog_client_contract_fnc_makeHVT` function within the HVTs' init field that links the unit to the HVT Task

```js
Arguments:
	0: OBJECT - The AI unit
	1: STRING - The ID of the task

Example:
	[this, "task_name"] call sog_client_contract_fnc_makeHVT
```

### Register Task
5. Register the HVT Task by calling the `sog_client_contract_fnc_hvt` function within the init field of the task

```js
Arguments:
	0: STRING - ID of the task
	1: STRING - Marker name for the extraction zone
	2: SCALAR - Number of hvts KIA or escaped to fail the task
	3: SCALAR - Number of captured or eliminated hvts to complete the task
	3: SCALAR - Amount of funds the company recieves if the task is successful
	4: SCALAR - Amount of rating the company and player lose if the task is failed
	5: SCALAR - Amount of rating the company and player recieve if the task is successful
	6: ARRAY - Array of task types to select from (Optional, default: [true, false])
	7: BOOLEAN - Should the mission end (MissionSuccess) if the task is successful (Optional, default: false)
	8: BOOLEAN - Should the mission end (MissionFailed) if the task is failed (Optional, default: false)
	9: SCALAR - Number of seconds before hvts escape (Optional)

Example:
	// Capture No Time Limit
	["task_name", "marker_name", 1, 2, 500000, -75, 300, [true, false], false, false] call sog_client_contract_fnc_hvt

	// Eliminate No Time Limit
	["task_name", "marker_name", 1, 2, 500000, -75, 300, [false, true], false, false] call sog_client_contract_fnc_hvt

	// Capture Within Time Limit
	["task_name", "marker_name", 1, 2, 500000, -75, 300, [true, false], false, false, 45] spawn sog_client_contract_fnc_hvt

	// Eliminate Within Time Limit
	["task_name", "marker_name", 1, 2, 500000, -75, 300, [false, true], false, false, 45] spawn sog_client_contract_fnc_hvt
```

## Links
[Home](framework/index) |
[Attack Module](framework/attack) |
[Defuse Module](framework/defuse) |
[Destroy Module](framework/destroy) |
[Hostage Module](framework/hostage) |
[HVT Module](framework/hvt)