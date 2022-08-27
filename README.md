# Ansible-AD

A repository of Ansible roles and playbooks using the ansible collection to manage Active Directory objects.&nbsp; Due to the fact that an injector configuration is used to authenticate to the exchange hybrid server from the target role server (a Domain Controller or PSWA server), the tasks that use the injected credentials in ```ansible.windows.win_powershell``` have the following attribute set on those tasks to protect passwords.

```yaml
   no_log: true
```

---

[`Credentials`](CREDENTIALS.md) information

 To use any of the Ansible-AD roles in this repository, you will need to create a new credential type to facilitate authentication.

**Name**: Active Directory  
**Input Configuration**:
  
   ```yaml
   fields:
     - id: username
       type: string
       label: AD Username
     - id: password
       type: string
       label: AD Password
       secret: true
     - id: domain
       type: string
       label: AD Domain
   ```

**Injector configuration**:

   ```yaml
   extra_vars:
     AD_DOMAIN: '{{ domain }}'
     AD_PASSWORD: '{{ password }}'
     AD_USERNAME: '{{ username }}'
   ```

Some role tasks send email to recipients and will require the creation of the following new credential type.&nbsp; This credential expects that the account that owns it has a mailbox and license in Microsoft 365. &nbsp; The from address will always be the UPN of this credential.

**Name**: Microsoft 365
**Input Configuration**:
  
   ```yaml
   fields:
     - id: userprincipalname
       type: string
       label: Microsoft 365 UPN
     - id: password
       type: string
       label: M365 User Password
       secret: true
   ```

**Injector configuration**:

   ```yaml
   extra_vars:
     M365_PASSWORD: '{{ password }}'
     M365_UPN: '{{ userprincipalname }}'
   ```

## Roles

This is the list of roles currently in this repository.&nbsp; The root main.yml file in each one requires one parameter - ```role_name```.

### Role: exchange-contact

This role is used to perform CRUD operations on Exchange Contact objects in Active Directory.&nbsp; It is designed for use in hybrid Exchange environments.

- #### Task: [`create`](exchange-contact/create/)

   Creates a new Exchange Contact.  

   This task is configured with the following variables:  
   | Description            | Variable name            | Required | Where specified       |
   | ---------------------- | ------------------------ |:--------:| --------------------- |
   | Contact First Name     | ```contact_first_name``` | yes      | extra_vars            |
   | Contact Last Name      | ```contact_last_name```  | yes      | extra_vars            |
   | External Email Address | ```contact_email```      | yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```       | yes      | role vars, extra_vars |
   | Contact OU Path        | ```contact_ou_path```    | yes      | role vars, extra_vars |

- #### Task: [`read`](exchange-contact/read/)

   Reads Exchange contacts from the directory.&nbsp; Will read one or more contacts, specified by any of the following identity values: Name, Alias, Distinguished name, Canonical DN, Email Address, or GUID.&nbsp; One or more recipients can be specified to recieve the report.&nbsp; Both the ```contact_identity``` and ```recipient_address``` variables are expected to be a [`list`](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#list-variables) variable.  

   This task is configured with the following variables:  
   | Description            | Variable name            | Required | Where specified       |
   | ---------------------- | ------------------------ |:--------:| --------------------- |
   | Contact identifier     | ```contact_identity```   | yes      | extra_vars            |
   | Exchange URI           | ```exchange_uri```       | yes      | role vars, extra_vars |
   | Recipient email address| ```recipient_address```  | yes      | extra_vars            |
   | Email host address     | ```smtp_host_name```     | yes      | role vars, extra_vars |
   | Email host port        | ```smtp_host_port```     | yes      | role vars, extra_vars |
