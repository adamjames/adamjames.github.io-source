adamjames.github.io
====================

These are the Jekyll and Markdown source files used to generate the content served at adamjames.github.io. They are stored seperately to the processed blog content in order to make forking and management easier.

A Vagrantfile for the virtual machine I use to build the blog is also included. You may wish to change it before you begin. 


Getting up and running
======================

Run `vagrant up` followed by `vagrant rsync-auto` in another Terminal tab once the machine is up and running to sync modified content back to the VM for processing.

SSH into the vagrant machine using `vagrant ssh`, then `cd /vagrant` and finally `jekyll serve --watch`. Jekyll should build the content and make it available at `http://localhost:8124`.


Plugins and Rsync
=================

If you allow the `_site` folder to be included in rsync-auto's file list (configurable in the Vagrantfile), the tag folder that the plugin generates will be lost when a change is made on the host machine. 

This is because the host folder and all subfolders are synchronised to the Vagrant machine when a change is made, and because the tag folders generated by the plugin are not present on the host - only within the VM - they are deleted. 

As soon as I have the time to work out a solution for this I'll update the repository with it. For now, I've found the best thing to do is to copy the _site folder that Jekyll generates directly from the VM to some folder on the host machine that is not being watched by the rsync-auto process. 


Publishing to Github Pages
==========================

Because this Jekyll blog uses plugins, you'll need to generate the static content (which ends up in the _site subdirectory by default) and then copy it into your {username}.github.com repository, commit it and push it.

Once you've built your static content, copy it from the VM's /vagrant folder into your Github Pages repository folder, commit the new content and push it to Github.

It is entirely possible for you to use Git from within the VM (via vagrant ssh) to publish to Github pages, but you'll need to set this up yourself.

If you're using `rsync-auto` to synchronise content between the Vagrant machine and the host, **do not** rely on the content of the `_site` folder on the host, as it is not kept up to date for reasons explained above.

Credits and License
===================

The theme is based on great CSS by <a href='https://github.com/hans/hans.github.com'>Hans Engel</a>. 

Where possible, I release the content of this site under the terms of <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a>.
