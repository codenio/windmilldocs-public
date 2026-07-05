---
slug: ansible-repo-ansible-cfg
title: Use a repo-provided ansible.cfg when delegating to a git repository
version: v1.744.0
tags: ['Script editor', 'Ansible']
description: Ansible scripts that delegate to a git repository can set the new ansible_cfg field, a repo-relative path to an ansible.cfg that becomes the effective configuration via ANSIBLE_CONFIG, so repo settings like roles paths, inventory plugins and callbacks apply. Windmill only re-applies runtime-bound settings (temp directories, vault password) and prepends its own roles and collections install paths. Requires workers running with DISABLE_NSJAIL=true; without the field, Windmill's generated config takes precedence as before.
features:
  [
    'New optional ansible_cfg field in the delegate_to_git_repo block, taking a path relative to the cloned repo root',
    'ANSIBLE_CONFIG points at the repo config so its roles paths, inventory plugins, callbacks, host_key_checking and ssh settings apply',
    'Windmill layers back only runtime-bound settings: temp/home directories in the job dir and vault password/identities from the script metadata',
    'Windmill-managed galaxy install locations are prepended to the roles_path and collections_path declared in the repo config',
    'The field supports {{ argname }} placeholders like playbook, commit and inventories_location',
    'The job fails with a clear error if the file is missing from the cloned repo; without the field, behavior is unchanged',
  ]
docs: /docs/getting_started/scripts_quickstart/ansible#using-the-repos-ansiblecfg
---
