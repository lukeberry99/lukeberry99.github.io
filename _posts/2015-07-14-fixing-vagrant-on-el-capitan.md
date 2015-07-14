---
layout: post
title: Fixing Vagrant on OSX 10.11 'El Capitan'
---

If you've updated to the latest release of OSX you might've noticed that Vagrant no longe wroks - even after a fresh install.

This is because _el capitan_ prevents anyone, including root, from writing to `/usr/bin` which is where Vagrant expects to be able to write it's executable.

Thankfully, fixing this is relatively straight forward, you just have to symlink the executable into `/usr/local/bin`. Here's how.

    sudo ln -s /opt/vagrant/bin/vagrant /usr/local/bin/vagrant
