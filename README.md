# Ansible-AD

A repository of Ansible roles and playbooks using the ansible collection to manage Active Directory objects.&nbsp; Due to the fact that an injector configuration is used to authenticate to the exchange hybrid server from the target role server (a Domain Controller or PSWA server), the tasks that use the injected credentials in ```ansible.windows.win_powershell``` have the following attribute set on those tasks to protect passwords.

```yaml
   no_log: true
```

---

View information about custom [`Credential`](docs/CREDENTIALS.md) types that are used in the tasks in this Ansible role.&nbsp; An Active Directory credential is needed to perform operations in AD.&nbsp; For plays that send email, a Sendgrid API key is required to send HTML reports.

## Roles

This is the list of roles currently in this repository.&nbsp; The root main.yml file in each one requires one parameter - ```role_name```.

- [`exchange-contact`](docs/EXCHANGE_CONTACT.md)

- [`exchange-distribution-group`](docs/EXCHANGE_DG.md)
