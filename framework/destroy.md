# Destroy Task Module

## Description
This module adds support for Destroy Tasks/Missions.

The mission maker must define target units, the framework will monitor the status of those units.

A threshold must be set, specifying the given amount of targets that have to be destroyed in order to complete the task.

The module can also trigger mission complete or mission fail.

## Usage
### Setup Object(s)
1. Setup the Destroy Task scene
2. Place down the target unit(s)
3. Call the `sog_client_contract_fnc_makeTarget` function within the targets' init field that links the unit to the Destroy Task

```js
Arguments:
	0: OBJECT - The AI unit or object
	1: STRING - The ID of the task

Example:
	[this, "task_name"] call sog_client_contract_fnc_makeTarget
```

### Register Task
4. Register the Destroy Task by calling the `sog_client_contract_fnc_destroy` function within the init field of the task

```js
Arguments:
	0: STRING - ID of the task
	1: SCALAR - Number of targets escaped to fail the task
	2: SCALAR - Number of targets destroyed to complete the task
	3: SCALAR - Amount of funds the company recieves if the task is successful
	4: SCALAR - Amount of rating the company and player lose if the task is failed
	5: SCALAR - Amount of rating the company and player recieve if the task is successful
	6: BOOLEAN - Should the mission end (MissionSuccess) if the task is successful (Optional, default: false)
	7: BOOLEAN - Should the mission end (MissionFailed) if the task is failed (Optional, default: false)
	8: SCALAR - Number of seconds before targets escape (Optional)

Example:
	// Default No Time Limit
	["task_name", 1, 2, 250000, -75, 300] call sog_client_contract_fnc_destroy

	// Destroy Within Time Limit
	["task_name", 1, 2, 250000, -75, 300, false, false, 45] spawn sog_client_contract_fnc_destroy
```

## Links
[Home](framework/index) |
[Attack Module](framework/attack) |
[Defuse Module](framework/defuse) |
[Destroy Module](framework/destroy) |
[Handler Module](framework/handler) |
[Hostage Module](framework/hostage) |
[HVT Module](framework/hvt)