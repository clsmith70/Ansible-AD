# Exchange Distribution Group tasks

[`Return`](/README.md) to main

## Description

This role is used to perform CRUD operations on Exchange Distribution Groups.&nbsp; It is designed for use in hybrid Exchange environments.  

- ### Task: [`create`](/exchange-distribution-group/create/)

  Creates a new Exchange distribution group.&nbsp; Valid group types are ```distribution``` or ```security```.  

   This task is configured with the following variables:  
   | Description            | Variable name            | Required | Where specified       |
   | ---------------------- | ------------------------ |:--------:| --------------------- |
   | Alias / SamAccountName | ```sam_account_name```   | yes      | extra_vars            |
   | Display Name           | ```display_name```       | yes      | extra_vars            |
   | Primary SMTP Address   | ```email_address```      | yes      | extra_vars            |
   | Group types            | ```group_type```         | yes      | extra_vars            |
   | Group OU Path          | ```group_ou_path```      | yes      | role vars, extra_vars |
   | Exchange URI           | ```exchange_uri```       | yes      | role vars, extra_vars |

- ### Task: [`read`](/exchange-distribution-group/read/)

  Reads the distribution group information from Active Directory.&nbsp; With the ```role_action``` parameter set to ```workflow```, the task will set_stats that can be used within a workflow to pass data.  If ```role_action``` is set to ```report```, an HTML report will be emailed to the recipient specified.  

   This task is configured with the following variables when ```role_action``` is set to ```workflow```:  
   | Description            | Variable name                    | Required | Where specified       |
   | ---------------------- | -------------------------------- |:--------:| --------------------- |
   | Group Identity         | ```distribution_group_identity```| yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```               | yes      | role vars, extra_vars |
  
   This task is configured with the following variables when ```role_action``` is set to ```report```:  
   | Description            | Variable name                    | Required | Where specified       |
   | ---------------------- | -------------------------------- |:--------:| --------------------- |
   | Group Identity         | ```distribution_group_identity```| yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```               | yes      | role vars, extra_vars |
   | Recipient email address| ```recipient_address```          | yes      | extra_vars            |
   | Sender Email Address   | ```from_address```               | yes      | role vars, extra_vars |
   | Sender Display Name    | ```from_name```                  | yes      | role vars, extra_vars |

[`Return`](/README.md) to main
