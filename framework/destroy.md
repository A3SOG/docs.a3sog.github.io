---
title: 'Documents - Destroy Task Module'
---

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
3. Call the `SOG_destroy_fnc_makeTarget` function within the targets' init field that links the unit to the Destroy Task

```js
Arguments:
	0: OBJECT - The AI unit or object
	1: STRING - The ID of the task

Example:
	[this, "task_name"] call SOG_destroy_fnc_makeTarget
```

### Register Task
4. Register the Destroy Task by calling the `SOG_destroy_fnc_registerDestroyTask` function within the init field of the task

```js
Arguments:
	0: STRING - ID of the task
	1: SCALAR - Number of targets escaped to fail the task
	2: SCALAR - Number of targets destroyed to complete the task
	3: BOOLEAN - Should the mission end (MissionSuccess) if the task is successful (Optional, default: false)
	4: BOOLEAN - Should the mission end (MissionFailed) if the task is failed (Optional, default: false)
	5: SCALAR - Number of seconds before targets escape (Optional)

Example:
	// Default No Time Limit
	["task_name", 1, 2, false] call SOG_destroy_fnc_registerDestroyTask

	// Destroy Within Time Limit
	["task_name", 1, 2, false, false, 45] spawn SOG_destroy_fnc_registerDestroyTask
```

## Links
[Home](framework/index) |
[Attack Module](framework/attack) |
[Destroy Module](framework/destroy) |
[Hostage Module](framework/hostage) |
[HVT Module](framework/hvt) |
[IED Module](framework/ied)