# FreeScout Custom Workflow User

This collection of files is designed to patch the original [FreeScout Workflow Module](https://freescout.net/module/workflows/).

## Why
The original Workflow Module uses a user named "Workflow" to execute all actions. Consequently, instead of displaying the name of the actual user, you see "Workflow" as the sender's name. 
You can alter the name in the .env file using the property WORKFLOWS_USER_FULL_NAME, but this has a few limitations. It only allows up to 20 characters, and additional settings, such as an email address, cannot be defined. As a result, signatures using variables like user.email are not displayed correctly. Additionally, when manually executing a workflow, the "Workflow" user is used instead of the user who initiated the workflow.

## What
This patch brings two enhancements:
- Define an existing user as the default user for all your automated workflows.
- Manual workflows will use the logged-in user running the workflow task as the sender.

## Requirements
You need a FreeScout installation and the Workflow Module installed.

## Installation
- Save a copy of your "Modules/Workflows" directory so that you can easily revert to the original.
- To define the default user used for your automated workflows, open your .env file in the root directory and add the following line anywhere in the file:
 WORKFLOWS_USER_EMAIL=existing-user@yourdomain.com
 **NOTE:** A User with this email /must/ exist in your FreeScout environment.
 Instead of using a real user's account, you may create a special account specifically for your workflows. For example:
  - First name: Bob
  - Last name: Doit
  - Email: bob.doit@yourdomain.com
  - Position: Support
  - ...
- Copy the files from this repository's "Workflows" directory into the "Modules/Workflows" directory of your FreeScout installation. 
The following files will be replaced:
  - Config/config.php
  - Entities/Workflow.php
  - Http/Controllers/WorkflowsController.php

## Note
If you have workflows that should not be associated with an existing user, it's advisable not to use this patch.

To undo this patch, use your backup.

To view the actual changes to the original, check [here](https://github.com/karrierekick-dev/freescout-custom-workflow-user/commit/bba3e06f98ca86e6e02e1f10977124d305541eab).

**Have fun!**
