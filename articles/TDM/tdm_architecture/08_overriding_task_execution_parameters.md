# Overriding Task Execution Parameters

The TDM API that [starts a task execution](/articles/TDM/tdm_gui/TDM_Basic_Task_Execution_APIs_Flow/04_execute_task_API.md) can get a list of parameter-value pairs to override the original value of these parameters on the task execution. 

This way, various of users can use a task as a template and change (override) the execution parameters without changing the task itself: each user can run the task on their environment and update the execution parameter based on their needs.

TDM 7.2 support the override of the following parameters:

- [TDM Environments](/articles/TDM/tdm_gui/07_tdm_gui_environment_overview.md): 
  - Source Environment on a [Extract task](/articles/TDM/tdm_gui/16_extract_task.md).
  - Source and/or Target Environments on a [Load task](/articles/TDM/tdm_gui/17_load_task_regular_mode.md).
- Globals: 
  - Adding Globals.
  - Updating the values of the [task's Globals](/articles/TDM/tdm_gui/23_task_globals_tab.md).

- [Entity List](/articles/TDM/tdm_gui/18_load_task_requested_entities_regular_mode.md#entities-list) : provide a list of entities separated by a comma instead of the task's entity list.
- [Selection  Method](/articles/TDM/tdm_gui/25_task_tdmdb_tables.md#requested-entities-columns) : set the overridden selection method to 'L' (Entity List), when overriding the task's Entity List.
- [Number of Entities](/articles/TDM/tdm_gui/17_load_task_regular_mode.md#number-of-entities) : change the number of entities to be processed by the task execution.

Note that the TDM supports overriding the task execution parameters only when invoking the start task execution API outside the TDM GUI. **Currently this option is not supported when executing the task using the TDM GUI.**

### Validate the Task Execution Parameters

The API validates the overridden parameters with the user's permissions on the task's environments:

- Overrides the source and/or target environments: check the user's permissions on the new environments and verify that the user has permissions to run the task on the environments.
- The task's environments are not overridden: check the user's permissions on the task's environments  and verify that the user has permissions to run the task on the environments.
- Overrides the Entity List or the Number of Entities: verify that the updated number of entities does not exceed the user's permissions on the environments on which the task needs to run. 

If at least one of the validation fails, the API does not start the task and returns the validation errors. 

### Task Execution Process

The override of task execution parameters does not update the task itself, but only impacts the given task execution:

The [task execution process](/articles/TDM/tdm_architecture/03_task_execution_processes.md) gets the overridden parameters from [task_execution_override_attrs](/articles/TDM/tdm_architecture/02_tdm_database.md#task_execution_override_attrs) TDM DB table and executes the task based on the overridden parameters.



[![Previous](/articles/images/Previous.png)](07_tdm_parameters_handling.md)



