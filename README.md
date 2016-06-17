# ansible

## How-Tos
#### How do I change passwords on multiple machines?

`hosts/inventory`
Change **${hosts}** to the hosts/machines on which you'd like to change passwords and
**${ssh_user}** to the username that is to be used on the remote machines.

`pc/pw.txt`
Change **${old_password}** to the default/current password on the machines and **${new_password}** to your desired password.

`pc/playbook.yml`
You can specify which group of machines from the inventory you'd like to send commands to. The playbook
is currently set to communicate with **all** hosts.

Run the following command:
```
ansible-playbook -i hosts/inventory pc/playbook.yml --extra-vars "srcfile=pc/pw.txt" --ask-pass
```
_You will be asked for your password to the remote machine._

#### How do I add my public key to authorized_keys on remote machines?

Replace `<your user name>` below and run the command to send your public key to all **dev** hosts:
```
ansible-playbook -i hosts/inventory auth/playbook.yml --extra-vars "ssh_user=<your user name>" --ask-pass
```