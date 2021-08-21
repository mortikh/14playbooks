# Playbooks
### About

You can find 2 playbooks there.
- First one for a creating user on remote server and place required SSH key onto.
- Second one for a postfix insallating\deleting on remote server.

### Files description

- `ansible.cfg` - Ansible configuration file. In our case it required only to specify inventory path.
- `hosts` - Inventory file. Specifying SSH access parameters of remote server.
- `user1key.pub` - Our SSH key for remote user. Please note, it's ecnrypted.
- `userssh.yml` - Playbook to create remote user and place SSH key into specified directory.
- `postfix.yml` - Playbook to install \ delete postfix on remote server.

### Usage
**userssh.yml**
Before you play pleas make sure that steps below were done:
- You generate SSH key for user you going to create
- Your SSH key ecnrypted with `ansible-vault encrypt YOURKEY.pub`

Please make sure that you change you using your own SSH details in `hosts` file.
`ansible-playbook userssh.yml --ask-vault-password`

Put your password once it will ask you for.

**postfix.yml**
Please make sure that you change you using your own SSH details in `hosts` file.

To install postfix:
`ansible-playbook postfix.yml -t "init postfix"`

To delte postfix:
`ansible-playbook postfix.yml -t "drop postfix"`
