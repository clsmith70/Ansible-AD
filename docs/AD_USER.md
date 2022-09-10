# User tasks

[`Return`](/README.md) to main

## Description

This role is used to perform CRUD operations on Active Directory user objects.&nbsp; The user creation crosses boundaries with the exchange based roles when creating FTEs in the directory.&nbsp; All FTEs in specified roles are required to have Active Directory accounts with related Microsoft 365 licenes and resources.

- ### ```role_name```: [`create`](/user/create/)

   Creates a new Active Directory user object.

  &nbsp;

  > #### create role variables
  >
  >    | Description            | Variable name                 | Required | Where specified       |
  >    | ---------------------- | ----------------------------- |:--------:| --------------------- |
  >    | First Name             | ```first_name```              | yes      | extra_vars            |
  >    | Middle Initial         | ```initials```                | no       | extra_vars            |
  >    | Last Name              | ```last_name```               | yes      | extra_vars            |
  >    | Department             | ```department```              | yes      | extra_vars            |
  >    | Job Title              | ```job_title```               | yes      | extra_vars            |
  >    | Exchange URI           | ```exchange_uri```            | yes      | role vars, extra_vars |
  >    | Contact OU Path        | ```department_user_ou_path``` | yes      | role vars, extra_vars |
  &nbsp;

- ### ```role_name```: [`read`](/user/read/)

- ### ```role_name```: [`update`](/user/update/)

- ### ```role_name```: [`delete`](/user/delete/)

[`Return`](/README.md) to main
