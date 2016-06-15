# ansible

## Some helpful How-Tos
* How do I change passwords on multiple machines?

`pc/inventory`
Change **${hosts}** to the hosts/machines on which you'd like to change passwords and
**${ssh_user}** to the username that is to be used on the remote machines.

`pc/pw.txt`
Change **${old_password}** to the default/current password on the machines and **${new_password}** to your desired password.

Run the following command from the directory **above** `pc/`:
```
ansible-playbook -i pc/inventory pc/playbook.yml --extra-vars "srcfile=pc/pw.txt" --ask-pass
```
You will be asked for your password to the remote machine.