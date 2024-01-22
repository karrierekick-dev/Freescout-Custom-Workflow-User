

# Freescout Custom Workflow User
This is a collection of files to patch the original [FreeScout Workflow Module](https://freescout.net/module/workflows/).

# Why
The original Workflow Module uses a user named "Workflow" to run all actions. So instead of a real user you get "Workflow" as the senders name. 
You may change the name in the .env file with the property WORKFLOWS_USER_FULL_NAME but this has a couple of limitations. Only up to 20 characters are possible and no further settings like an email adress can be defined, so signatures using variables like user.email are not shown correctly.
When running a workflow manually, this "Workflow" user will be used as well instead of the user who started the workflow.

# What
It will bring 2 enhancements
* Define an existing user as the default user for all your automated workflows
* Manual workflows will use the logged in user running the workflow task as the sender.

# Requirements
You need a FreeScout installation and the Workflow Module being installed.

# Installation
* Please save a copy of your "Modules/Workflows" directory so you may easily go back to the original.
* To define the default user which will be used for your automated workflows, open your .env file in the root directory and add the following line anywhere in the file
  WORKFLOWS_USER_EMAIL=existing-user@yourdomain.com
* Copy the files from this repository's "Workflows" directory into the "Modules/Workflows" directory of your FreeScout installation. 
The following files will be replaced
  * Config/config.php
  * Entities/Workflow.php
  * Http/Controllers/WorkflowsController.php

# Note
If you have Workflows which should not be related to an existing user, you should not use this patch.

Instead of using a real users account, you may create a special account only for your workflows. Something like 
first name: Bob 
last name: Doit
email: bob.doit@yourdomain.com
position: Support
...

To undo this patch, use your backup.

**Have fun**


