# Role Minimal Backup #

This role is intended to do a one shot backup of hosts in the Ansible inventory. Think of a situation where you are migration a service from one host to another. But you don't want to loose any manual work you've done on the old host. Like history files, local scripts etc. Of course it's better to have everything managed via configuration management and version management but experience tells there will always be this one host full of manual testing, scripting and hacking you have to take care of.

## How it works ##

The role will create a local temporary directory where all data will end up. Per default it will just fetch information about all hosts, like size and fill level of volumes, size of interesting directories, etc. When you run it with certain variables set (see below) it will also create archives of directories and files and fetch them to the Ansible command host.

## Caveats ##

* If you add a directory as an exception (not to archive and fetch it), the role will stop fetching *new* data. If there already is an archive of that directory it will always fetch that one to the command host.
