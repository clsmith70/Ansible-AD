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
   | Description            | ```description```        | yes      | extra_vars            |
   | Group types            | ```group_type```         | yes      | extra_vars            |
   | Group OU Path          | ```group_ou_path```      | yes      | role vars, extra_vars |
   | Exchange URI           | ```exchange_uri```       | yes      | role vars, extra_vars |
   
   [`Return`](/README.md) to main
