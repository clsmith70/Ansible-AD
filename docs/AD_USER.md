# User tasks

[`Return`](/README.md) to main

## Description

This role is used to perform CRUD operations on Active Directory user objects.&nbsp; When a new user account requires a license, this playbook should be part of a workflow that includes the appropriate additional playbooks to add a remote mailbox, add a license, and apply any requried mailbox policies.

- ### ```role_name```: [`create`](/user/create/)

   Creates a new Active Directory user object depending on which ```role_action``` is defined.&nbsp; The valid values for ```role_action``` are ```named_user``` and ```service_user```.&nbsp; The ```service_user``` action creates an AD User object for use with applications that do not support the more secure group managed service account.

  &nbsp;

  > #### variables when ```role_action``` == '```named_user```'
  >
  >    | Description            | Variable name                 | Required | Where specified       |
  >    | ---------------------- | ----------------------------- |:--------:| --------------------- |
  >    | Employee ID Number     | ```employee_id```             | yes      | extra_vars            |
  >    | First Name             | ```first_name```              | yes      | extra_vars            |
  >    | Middle Initial         | ```initials```                | no       | extra_vars            |
  >    | Last Name              | ```last_name```               | yes      | extra_vars            |
  >    | Department             | ```department```              | yes      | extra_vars            |
  >    | Job Title              | ```job_title```               | yes      | extra_vars            |
  >    | User Email to Notify   | ```notification_address```    | yes      | extra_vars            |
  >    | Email Suffix           | ```email_domain```            | yes      | role vars, extra_vars |
  >    | Remote Routing Suffix  | ```remote_routing_domain```   | yes      | role vars, extra_vars |
  >    | Department User OU Path| ```department_user_ou_path``` | yes      | role vars, extra_vars |
  &nbsp;

  > #### variables when ```role_action``` == '```service_user```'
  >
  >    | Description            | Variable name              | Required | Where specified       |
  >    | ---------------------- | -------------------------- |:--------:| --------------------- |
  >    | Application Name       | ```display_name```         | yes      | extra_vars            |
  >    | Department             | ```department```           | yes      | extra_vars            |
  >    | Internal Suffix        | ```email_domain```         | yes      | role vars, extra_vars |
  >    | Service User OU Path   | ```service_user_ou_path``` | yes      | role vars, extra_vars |
  >    | User Email to Notify   | ```notification_address``` | yes      | extra_vars            |
  &nbsp;

- ### ```role_name```: [`read`](/user/read/)

- ### ```role_name```: [`update`](/user/update/)

  Updates a user object with values provided.&nbsp; The task that is run depends on the attribute being altered.&nbsp; Some attributes, like extensionAttribute1, are set using the Add, Remove, Replace and Clear PowerShell parameters.&nbsp; The task that is run is decided by the value of the ```role_action``` parameter.&nbsp; The valid values for ```role_action``` are ```add_attribute``` (can add or change), ```remove_attribute``` (clears attributes), and ```transfer_promote``` (sets title and/or department).

  > #### variables when ```role_action``` == '```add_attribute```'
  >
  >    | Description            | Variable name              | Required | Where specified       |
  >    | ---------------------- | -------------------------- |:--------:| --------------------- |
  >    | User Id                | ```sam_account_name```     | yes      | extra_vars            |
  >    | List of attributes     | ```attribute_setstring```  | yes      | extra_vars            |
  >
  >```attribute_setstring``` with one name/value pair: '```extensionAttribute12=value0```'  
  >```attribute_setstring``` with mutiple name/value pairs: '```extensionAttribute1=value5;extensionAttribute4=value2```'

  &nbsp;  

  > #### variables when ```role_action``` == '```remove_attribute```'
  >
  >    | Description            | Variable name              | Required | Where specified       |
  >    | ---------------------- | -------------------------- |:--------:| --------------------- |
  >    | User Id                | ```sam_account_name```     | yes      | extra_vars            |
  >    | List of attributes     | ```attribute_setstring```  | yes      | extra_vars            |
  >
  >```attribute_setstring``` with one attribute to clear: '```extensionAttribute12```'  
  >```attribute_setstring``` with mutiple attributes to clear: '```extensionAttribute1,extensionAttribute4```'

  &nbsp;

  > #### variables when ```role_action``` == '```change_password```'
  >
  >    | Description            | Variable name              | Required | Where specified       |
  >    | ---------------------- | -------------------------- |:--------:| --------------------- |
  >    | User Id                | ```sam_account_name```     | yes      | extra_vars            |

  &nbsp;

- ### ```role_name```: [`delete`](/user/delete/)

[`Return`](/README.md) to main
