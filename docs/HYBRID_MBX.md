# Hybrid (on-premises) Mailbox tasks

[`Return`](/README.md) to main

## Description

This role is used to add or remove mailbox parameters to/from AD User objects on-premises.&nbsp; This role is designed to be used as part of a workflow and should not be used by itself.

- ### ```role_name```: [`create`](/hybrid-mailbox/create/)

   Sets the standard mailbox policy settings on a remote mailbox depending on which ```role_task``` is defined.&nbsp; The current valid value for ```role_task``` is ```user```.

  &nbsp;

  > #### variables when ```role_task``` == '```user```'
  >
  >    | Description                  | Variable name                           | Required | Where specified       |
  >    | ---------------------------- | --------------------------------------- |:--------:| --------------------- |
  >    | New User Sam Account Name    | ```new_user_info.sam_account_name```    | yes      | stats                 |
  >    | New User User Principal Name | ```new_user_info.user_principal_name``` | yes      | stats                 |
  >    | Microsoft 365 Routing Domain | ```m365_routing_domain```               | yes      | role_vars, extra_vars |
  >    | Exchange URI                 | ```exchange_uri```                      | yes      | role vars, extra_vars |
  &nbsp;

[`Return`](/README.md) to main
