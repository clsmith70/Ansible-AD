# Ansible-AD

A repository of Ansible roles and playbooks using the ansible collection to manage Active Directory objects.&nbsp; Due to the fact that an injector configuration is used to authenticate to the exchange hybrid server from the target role server (a Domain Controller or PSWA server), the tasks that use the injected credentials in ```ansible.windows.win_powershell``` have the following attribute set on those tasks to protect passwords.

```yaml
   no_log: true
```

This initial version targets the 2008 R2 and older functional levels of Microsoft Active Directory as needed for current projects.&nbsp; In these older versions of Active Directory, PowerShell must be employed due to the fact that many of the newer modules, like [`community.windows.win_domain_user`](https://docs.ansible.com/ansible/latest/collections/community/windows/win_domain_user_module.html), error out or run incompletely.&nbsp; A future version of this repository will be created to target newer functional levels in the near future.

---

&nbsp;

## Custom credentials

View information about custom [`Credential`](docs/CREDENTIALS.md) types that are used in the tasks in this Ansible role.&nbsp; An Active Directory credential is needed to perform operations in AD.&nbsp; For plays that send email, a Sendgrid API key is required to send HTML reports.

&nbsp;

## Roles

This is the list of roles currently in this repository.&nbsp; The root main.yml file in each one requires one parameter - ```role_name```.

- [`exchange-contact`](docs/EXCHANGE_CONTACT.md)
- [`exchange-distribution-group`](docs/EXCHANGE_DG.md)
- [`user`](docs/AD_USER.md)
