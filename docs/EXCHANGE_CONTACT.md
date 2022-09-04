# Exchange Contact tasks

[`Return`](/README.md) to main

## Description

This role is used to perform CRUD operations on Exchange Contact objects in Active Directory.&nbsp; It is designed for use in hybrid Exchange environments.&nbsp; These tasks can be extended to include other parameters, like CustomAttribute1-14 for example, to meet any organizational needs or standards.

- ### ```role_name```: [`create`](/exchange-contact/create/)

   Creates a new Exchange Contact.  

  &nbsp;

  > #### create role variables
  >
  >    | Description            | Variable name            | Required | Where specified       |
  >    | ---------------------- | ------------------------ |:--------:| --------------------- |
  >    | Contact First Name     | ```contact_first_name``` | yes      | extra_vars            |
  >    | Contact Last Name      | ```contact_last_name```  | yes      | extra_vars            |
  >    | External Email Address | ```contact_email```      | yes      | extra_vars            |
  >    | Exchange URI           | ```exchange_uri```       | yes      | role vars, extra_vars |
  >    | Contact OU Path        | ```contact_ou_path```    | yes      | role vars, extra_vars |
  &nbsp;

- ### ```role_name```: [`read`](/exchange-contact/read/)

   Reads Exchange contacts from the directory.&nbsp; Will read one or more contacts, specified by any of the following identity values: Name, Alias, Distinguished name, Canonical DN, Email Address, or GUID.&nbsp; One or more recipients can be specified to recieve the report.&nbsp; Both the ```contact_identity``` and ```recipient_address``` variables are expected to be a [`list`](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#list-variables) variable.  

  &nbsp;

  > #### read role variables
  >
  >    | Description            | Variable name            | Required | Where specified       |
  >    | ---------------------- | ------------------------ |:--------:| --------------------- |
  >    | Contact identifier     | ```contact_identity```   | yes      | extra_vars            |
  >    | Exchange URI           | ```exchange_uri```       | yes      | role vars, extra_vars |
  >    | Recipient email address| ```recipient_address```  | yes      | extra_vars            |
  >    | Sender Email Address   | ```from_address```       | yes      | role vars, extra_vars |
  >    | Sender Display Name    | ```from_name```          | yes      | role vars, extra_vars |
  &nbsp;

- ### ```role_name```: update

   Due to the complexity of covering multiple scenarios, the update task is being omitted.&nbsp; Updates should be left to administrators or be handled as a delete/recreate operation.
&nbsp;

&nbsp;

- ### ```role_name```: [`delete`](/exchange-contact/delete/)

   Deletes Exchange contacts from the directory&nbsp; Will delete one or more contacts, specified by any of the following identity values: Name, Alias, Distinguished name, Canonical DN, Email Address, or GUID.&nbsp; The ```contact_identity``` variable is expected to be a [`list`](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#list-variables) variable.  

  &nbsp;

  > #### delete role variables
  >
  >    | Description            | Variable name            | Required | Where specified       |
  >    | ---------------------- | ------------------------ |:--------:| --------------------- |
  >    | Contact identifier     | ```contact_identity```   | yes      | extra_vars            |
  >    | Exchange URI           | ```exchange_uri```       | yes      | role vars, extra_vars |
  &nbsp;

   [`Return`](/README.md) to main
