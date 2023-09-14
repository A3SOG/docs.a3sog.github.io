# Handle Task Module

## Description
This module adds a handler for Tasks/Missions.

## Usage
### Register Task
1. Register the type of task by calling the `sog_client_contract_fnc_handler` function within the init field of the task

```js
Arguments:
	0: STRING - Type of task
	1: ARRAY - Array of params for the task (see ea. task module for params)
	2: SCALAR - Amount of rating required for task (Optional)

Example:
	// HVT No Time Limit
	["hvt", ["task_1", 2, 1, "", 500000, -75, 300, [false, true]], 250] remoteExec ["sog_client_contract_fnc_handler", 2, false];
```

## Links
[Home](framework/index) |
[Attack Module](framework/attack) |
[Defuse Module](framework/defuse) |
[Destroy Module](framework/destroy) |
[Handler Module](framework/handler) |
[Hostage Module](framework/hostage) |
[HVT Module](framework/hvt)