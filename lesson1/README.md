# [ATS](http://www.atsid.com) SaltStack Introductory Training.
## First presented: 2014-03-06

The following outlines our learning objectives for this training session. 
Upon successfully completing this training, participants will be able to:

### Introduction

* Explain the infrastructure automation problem Salt is designed to address 
* Describe the salt master/minion architecture
* Manage minion registration including:
    * Registering a new minion with a master
    * Identify all registered minions
    * Pre-seed a minion with a key
* Execute remote commands on all or some minions
* Gather system information from a minion
* Explain which commands/processes execute on a master versus on the minion


### Salt States

* Organize state (sls) files in a consistent directory structure per conventions
* Create a self-contained state (sls) file to accomplish a goal
* Use the pkg state to install software on minions
* Use the file state to manage files on minions
* Use the service state to manage services
* Use the 'require' attribute to ensure ordering of state application
* Use the dry-run test=True argument to test states
* Use the SaltStack documentation to look up options for a state
