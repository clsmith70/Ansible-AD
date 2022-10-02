# Exchange Online (Remote) Mailbox tasks

[`Return`](/README.md) to main

## Description

This role is used to perform set and recovery tasks for remote mailboxes in Exchange Online (M365).&nbsp; This role is designed to be used as part of a workflow and should not be used by itself.

- ### ```role_name```: [`set`](/exo-mailbox/set/)

   Sets the standard mailbox policy settings on a remote mailbox depending on which ```role_task``` is defined.&nbsp; The current valid value for ```role_task``` is ```standard```.

  &nbsp;

  > #### variables when ```role_task``` == '```standard```'
  >
  >    | Description               | Variable name                        | Required | Where specified  |
  >    | ------------------------- | ------------------------------------ |:--------:| ---------------- |
  >    | New User Sam Account name | ```new_user_info.sam_account_name``` | yes      | stats            |
  &nbsp;

[`Return`](/README.md) to main
