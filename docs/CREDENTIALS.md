# Credentials

 To use any of the Ansible-AD roles in this repository, you will need to create a new credential type to facilitate authentication.

[`Return`](/README.md) to main

---

## **Name**: Active Directory  

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

---

## **Name**: Sendgrid API Key  

**Input Configuration**:
  
   ```yaml
   fields:
     - id: api_key
       type: string
       label: Sendgrid API Key
       secret: true
   ```

**Injector configuration**:

   ```yaml
   extra_vars:
     SENDGRID_API_KEY: '{{ api_key }}'
   ```

---

[`Return`](/README.md) to main
