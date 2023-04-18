ansible-silverblue
==================

This is my personal ansible playbook for whenever I need/want to reinstall Fedora Silverblue.

Included Roles
--------------

The main parts of this project can be seen in the 'roles' directory. Each role included there
contains a README file that explains what the role is and how to use it. For starters, here is a
brief summary of each role:

  - layered_packages: Install or remove packages into / from the base rpm-ostree image.
  - flatpaks: Install desired [flatpak](https://flatpak.org/) applications.
  - fonts: Install custom fonts (this role is under the GPLv3 License).
  - os_updates: Configure the auto-update policy for the host.

Variables
---------

All the project's variables are in the `group_vars/all` file. This makes it easy to
update the project's variables from a single location.

Setup
-----
To do right after a fresh install of [Silverblue SwayWM spin (sericea)](https://fedoraproject.org/sericea/):

```
# install git needed to fetch this repo
rmp-ostree install git 
# reboot to apply changes
systemctl reboot
# clone this repo
git clone https://github.com/GDay/ansible-silverblue
# set up ansible
cd ansible-silverblue
python3 -m venv venv
source venv/bin/activate
pip3 install -r requirements.txt
ansible-galaxy collection install -r requirements.yml
```

Run the Playbooks
-----------------

This command will run all of the included playbooks:

`ansible-playbook -i hosts -l this_host -K -v playbook_base.yml`

Roles can be run individually, see that role's `README` file for the needed command.

License
-------

Unless otherwise indicated in the individual role, this project is under the BSD License.


Credits
-------

This setup has been based of Jim Campbell's example which can be found here: https://github.com/j1mc/ansible-silverblue
