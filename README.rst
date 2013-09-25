Vagrant VM quickstart for Python projects
=========================================

Basic config and provisioning scripts for bootstrapping a VM to run a
Python project.

Installs:
 - essential Python packages and PostgreSQL database server & client on
   the system
 - PyPI packages from a ``requirements`` file to a virtualenv

Sets up some reasonable default choices assuming you want to be able to
access the project repository via the filesystem and access a dev server
running on the VM via the browser on the host.

Usage
-----

First up, get a copy of the repo::

  $ mkdir -p ~/boxes/pyvm
  $ cd ~/boxes/pyvm
  $ git clone https://github.com/mattoc/python-vm-quickstart.git

Edit the ``Vagrantfile`` and replace the paths as necessary for the 
``config.vm.synced_folder`` var for your local and desired remote path.

Update the Ansible ``playbook.yml`` and set the ``project_alias`` to
match your own project's root directory name.

::

  $ vagrant up
  [... waiting ...]
  $ vagrant ssh
  ...
  (myproject)vagrant@precise32:~$ 

And you should be ready to go!

For a Django project:

::
  
  (myproject)vagrant@precise32:~$ cd myproject
  (myproject)vagrant@precise32:~$ python manage.py runserver 0.0.0.0:8000

Visit http://localhost:54321 on the host and you should see the app
served by the Django development server running on the VM.

Prerequisites
-------------

On the host machine you'll need VirtualBox (or another VM provider), 
Vagrant and Ansible installed.
