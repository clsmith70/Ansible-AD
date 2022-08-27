# Ansible-AD

A repository of Ansible roles and playbooks using the ansible collection to manage Active Directory objects.&nbsp; Due to the fact that an injector configuration is used
to authenticate to the exchange hybrid server from the target role server (a Domain Controller or PSWA server), the tasks that use the injected credentials are set to use

```yaml
   no_log: true
```

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

## Roles

This is the list of roles currently in this repository.&nbsp; The root main.yml file in each one requires one parameter - ```role_name```.

### Role: exchange-contact

This role is used to perform CRUD operations on Exchange Contact objects in Active Directory.&nbsp; It is designed for use in hybrid Exchange environments.

- ### Task: [`create`](exchange-contact/create/tasks/)

   Creates a new Exchange Contact.&nbsp; It requires the following information:  
   | Description            | Jinja2 variable name     |
   | ---------------------- | ------------------------ |
   | Contact First Name     | ```contact_first_name``` |
   | Contact Last Name      | ```contact_last_name```  |
   | External Email Address | ```contact_email```      |
   | Exchange URI           | ```exchange_uri```       |
   | Contact OU Path        | ```contact_ou_path```    |
