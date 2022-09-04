# Exchange Distribution Group tasks

[`Return`](/README.md) to main

## Description

This role is used to perform CRUD operations on Exchange Distribution Groups.&nbsp; It is designed for use in hybrid Exchange environments.  

- ### Task: [`create`](/exchange-distribution-group/create/)

  Creates a new Exchange distribution group.&nbsp; Valid group types are ```distribution``` or ```security```.  

  &nbsp;

- #### variables

   | Description            | Variable name            | Required | Where specified       |
   | ---------------------- | ------------------------ |:--------:| --------------------- |
   | Alias / SamAccountName | ```sam_account_name```   | yes      | extra_vars            |
   | Display Name           | ```display_name```       | yes      | extra_vars            |
   | Primary SMTP Address   | ```email_address```      | yes      | extra_vars            |
   | Group types            | ```group_type```         | yes      | extra_vars            |
   | Group OU Path          | ```group_ou_path```      | yes      | role vars, extra_vars |
   | Exchange URI           | ```exchange_uri```       | yes      | role vars, extra_vars |
  &nbsp;

- ### Task: [`read`](/exchange-distribution-group/read/)

  Reads the distribution group information from Active Directory.&nbsp; With the ```role_action``` parameter set to ```workflow```, the task will set_stats that can be used within a workflow to pass data.  If ```role_action``` is set to ```report```, an HTML report will be emailed to the recipient specified.  

  &nbsp;

- #### variables  when ```role_action``` == '```workflow```'

   | Description            | Variable name                    | Required | Where specified       |
   | ---------------------- | -------------------------------- |:--------:| --------------------- |
   | Group Identity         | ```distribution_group_identity```| yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```               | yes      | role vars, extra_vars |
  
  &nbsp;

- #### variables when ```role_action``` == '```report```'

   | Description            | Variable name                    | Required | Where specified       |
   | ---------------------- | -------------------------------- |:--------:| --------------------- |
   | Group Identity         | ```distribution_group_identity```| yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```               | yes      | role vars, extra_vars |
   | Recipient email address| ```recipient_address```          | yes      | extra_vars            |
   | Sender Email Address   | ```from_address```               | yes      | role vars, extra_vars |
   | Sender Display Name    | ```from_name```                  | yes      | role vars, extra_vars |
  &nbsp;

- ### Task: [`update`](/exchange-distribution-group/update/)

  Updates the DisplayName or group membership depending on which ```role_action``` is set.  The valid values for ```role_action``` are ```set_display_name```, ```add_member```, and ```remove_member```.&nbsp A workflow can be used to replace distribution group members with calls to add and remove member separately.&nbsp; The value(s) provided in ```add_user``` or ```remove_user``` are expected to be [`list`](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#list-variables) variables.&nbsp; To report the state before and/or after the change, use the read task with ```role_action``` set to report.

  &nbsp;

- #### variables when ```role_action``` == '```set_display_name```'

   | Description            | Variable name                    | Required | Where specified       |
   | ---------------------- | -------------------------------- |:--------:| --------------------- |
   | Group Identity         | ```distribution_group_identity```| yes      | extra_vars            |
   | Display Name           | ```display_name```               | yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```               | yes      | role vars, extra_vars |

  &nbsp;

- #### variables when ```role_action``` == '```add_member```'

   | Description            | Variable name                    | Required | Where specified       |
   | ---------------------- | -------------------------------- |:--------:| --------------------- |
   | Group Identity         | ```distribution_group_identity```| yes      | extra_vars            |
   | User(s) to add         | ```add_user```                   | yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```               | yes      | role vars, extra_vars |

  &nbsp;

- #### variables when ```role_action``` == '```remove_member```'

   | Description            | Variable name                    | Required | Where specified       |
   | ---------------------- | -------------------------------- |:--------:| --------------------- |
   | Group Identity         | ```distribution_group_identity```| yes      | extra_vars            |
   | User(s) to remove      | ```remove_user```                | yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```               | yes      | role vars, extra_vars |
  &nbsp;

[`Return`](/README.md) to main
