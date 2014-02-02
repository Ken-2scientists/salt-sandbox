Salt Sandbox
============

This project sets up a multi-machine Vagrant file for the purpose of exploring Salt_.

.. _Salt: http://www.saltstack.com

To get started, launch and login to the master: ::

    vagrant up master
    vagrant ssh master
    sudo salt-key -L

You should see output showing no keys at present: ::

    vagrant@salt:~$ sudo salt-key -L
    Accepted Keys:
    Unaccepted Keys:
    Rejected Keys:

That command should confirm that the salt-master was successfully installed, and that,
at present, no minions have attempted to check in to the master. Both the salt-master
and the single minion have been configured with private (host-only) networking on the 
same subnet, allowing them to communicate with one another. The `/etc/hosts` file for
both has been configured so that they know of each other as `salt` and `minion`,
respectively.

In a separate terminal window, start and login to the minion: ::

    vagrant up minion
    vagrant ssh minion

In the original (master) window, check to see that the minion has checked in: ::

    vagrant@salt:~$ sudo salt-key -L
    Accepted Keys:
    Unaccepted Keys:
    minion
    Rejected Keys:

Finally, accept the minion's key: ::

    vagrant@salt:~$ sudo salt-key -A
    The following keys are going to be accepted:
    Unaccepted Keys:
    minion
    Proceed? [n/Y] Y

The following will confirm that the salt-master is able to reach all minion(s): ::

    vagrant@salt:~$ sudo salt \* test.ping
    minion:
        True
