Salt Sandbox
============

This project sets up a multi-machine Vagrant file for the purpose of exploring Salt_.
.. _Python: http://www.saltstack.com

To use: ::

    vagrant up master
    vagrant up minion

You can then (ideally in separate terminal sessions) login: ::

    vagrant ssh master
    vagrant ssh minion
