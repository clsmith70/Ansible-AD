# Ansible-AD

A repository of Ansible roles and playbooks using the ansible collection to manage Active Directory objects.&nbsp; Due to the fact that an injector configuration is used to authenticate to the exchange hybrid server from the target role server (a Domain Controller or PSWA server), the tasks that use the injected credentials in ```ansible.windows.win_powershell``` have the following attribute set on those tasks to protect passwords.

```yaml
   no_log: true
```

---

View information about custom [`Credential`](CREDENTIALS.md) types that are used in the tasks in this Ansible role.&nbsp; An Active Directory credential is needed to perform operations in AD.&nbsp; For plays that send email, a Sendgrid API key is required to send HTML reports.

## Roles

This is the list of roles currently in this repository.&nbsp; The root main.yml file in each one requires one parameter - ```role_name```.

### Role: exchange-contact

This role is used to perform CRUD operations on Exchange Contact objects in Active Directory.&nbsp; It is designed for use in hybrid Exchange environments.&nbsp; These tasks can be extended to include other parameters, like CustomAttribute1-14 for example, to meet any organizational needs or standards.

- ### Task: [`create`](exchange-contact/create/)

   Creates a new Exchange Contact.  

   This task is configured with the following variables:  
   | Description            | Variable name            | Required | Where specified       |
   | ---------------------- | ------------------------ |:--------:| --------------------- |
   | Contact First Name     | ```contact_first_name``` | yes      | extra_vars            |
   | Contact Last Name      | ```contact_last_name```  | yes      | extra_vars            |
   | External Email Address | ```contact_email```      | yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```       | yes      | role vars, extra_vars |
   | Contact OU Path        | ```contact_ou_path```    | yes      | role vars, extra_vars |

- ### Task: [`read`](exchange-contact/read/)

   Reads Exchange contacts from the directory.&nbsp; Will read one or more contacts, specified by any of the following identity values: Name, Alias, Distinguished name, Canonical DN, Email Address, or GUID.&nbsp; One or more recipients can be specified to recieve the report.&nbsp; Both the ```contact_identity``` and ```recipient_address``` variables are expected to be a [`list`](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#list-variables) variable.  

   This task is configured with the following variables:  
   | Description            | Variable name            | Required | Where specified       |
   | ---------------------- | ------------------------ |:--------:| --------------------- |
   | Contact identifier     | ```contact_identity```   | yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```       | yes      | role vars, extra_vars |
   | Recipient email address| ```recipient_address```  | yes      | extra_vars            |

- ### Task: update

   Due to the complexity of covering multiple scenarios, the update task is being omitted.&nbsp; Updates should be left to administrators or be handled as a delete/recreate operation.

- ### Task: [`delete`](exchange-contact/delete/)

   Deletes Exchange contacts from the directory&nbsp; Will delete one or more contacts, specified by any of the following identity values: Name, Alias, Distinguished name, Canonical DN, Email Address, or GUID.&nbsp; The ```contact_identity``` variable is expected to be a [`list`](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#list-variables) variable.  

   This task is configured with the following variables:  
   | Description            | Variable name            | Required | Where specified       |
   | ---------------------- | ------------------------ |:--------:| --------------------- |
   | Contact identifier     | ```contact_identity```   | yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```       | yes      | role vars, extra_vars |
