# Exchange Online (Remote) Mailbox tasks

[`Return`](/README.md) to main

## Description

This role is used to perform set and recovery tasks for remote mailboxes in Exchange Online (M365).&nbsp; This role is designed to be used as part of a workflow and should not be used by itself, except when using the get task.

- ### ```role_name```: [`update`](/exo-mailbox/update/)

   Sets the standard mailbox policy settings on a remote mailbox depending on which ```role_task``` is defined.&nbsp; The current valid value for ```role_task``` is ```standard```.

  &nbsp;

  > #### variables when ```role_task``` == '```standard```'
  >
  >    | Description               | Variable name                        | Required | Where specified  |
  >    | ------------------------- | ------------------------------------ |:--------:| ---------------- |
  >    | New User Sam Account name | ```new_user_info.sam_account_name``` | yes      | stats            |
  &nbsp;

- ### ```role_name```: [`read`](/exo-mailbox/read/)

    Gets the current state and settings for a specified mailbox.&nbsp; The inactive variable, when set, indicates that inactive or offline mailboxes should be checked.&nbsp; This can be used after a search of online mailboxes has returned no results.

  &nbsp;

  > #### variables for the get role
  >
  >    | Description                            | Variable name  | Required | Where specified  |
  >    | -------------------------------------- | -------------- |:--------:| ---------------- |
  >    | Alias / SamAccountName / Email Address | ```identity``` | yes      | stats            |
  >    | Inactive Search (true/false)           | ```inactive``` | yes      | extra_vars       |
  &nbsp;

[`Return`](/README.md) to main
