# idm_ops

This is a collection of playbooks you can use to administer Red Hat IDM servers with Ansible.  It takes advantage of the redhat/rhel_idm collection.  

# Using the requirements.yml
A requirements.yml file is included which can be used to install the collection dependencies via ansible-galaxy or via project checkout in Ansible Tower.

### With Ansible Galaxy
If you are using the upstream Ansible project or Ansible Engine you can install the collection requirements via ansible-galaxy:

```
$ ansible-galaxy install -r collections/requirements.yml
```

This will install the collection to the default directory for collections on your ansible control node.

# vault.yml
You will need to replace the variable file named vault.yml and ensure you set the idm_ops_admin_password variable to your IDM administrator password.  If you use a service account for administration of your ipa infrastructure, additionally add a line with the idm_ops_admin_username variable set to the username of the service account.


```yaml
---
# idm_ops_admin_username: <username>
idm_ops_admin_password: <password>
```

You should encrypt this file using ansible-vault to ensure the credentials are not stored in clear text.

If you're using Automation Controller, you will need to create a credential to decrypt this vaulted variable file.  That credential will need to be used along with a machine credential in your job template.