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

- ### ```role_name```: [`delete`](/user/delete/)

[`Return`](/README.md) to main