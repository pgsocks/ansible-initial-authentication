Assuming Ansible can log into the remote host as root, this playbook will add
an ansible user with passwordless sudo and an authorized key for SSH access. It
will then disable root login and password challenge authentication for SSH.

# Usage

Run `ansible-playbook` and set the `pub_key` variable.

```
ansible-playbook -e pub_key="{{ lookup('file', 'id_rsa.pub') playbook.yml }}"
```

If no key file is given, then the ansible user will authorize the `id_rsa.pub`
key of the user who runs `ansible-playbook`.

The `init` tag can be used to only create an ansible user without disabling
root login etc. The `secure` tag can be used to only disable root login and
password challenge, which is useful if the ansible user is already created.
