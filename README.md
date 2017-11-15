# Curated list of Ansible roles, frecklecutables and freckelize adapters

This repository contains a collection of [Ansible roles](http://ansible-docs.readthedocs.io/zh/stable-2.0/rst/playbooks_roles.html), [frecklecutables](https://docs.freckles.io/en/latest/frecklecute_command.html#frecklecutables) and [freckelize adapters](https://docs.freckles.io/en/latest/freckelize_command.html#adapters-profiles) which can be considered useful for a wider audience.

It is assembled using the [`git subtree` command](https://www.atlassian.com/blog/git/alternatives-to-git-submodule-git-subtree), which is why whoever contributes to this repository should try to avoid mixing commits that relate to several different (remote) git repositories.

To make adding and updating new remote subtree repositories containing Ansible roles easier, this repository contains a helper script called 'repo-manage':

## `repo-manage`

Usage:

```
./repo-manage add -p <local_path_to_folder> <repo_url>
```

Or, if you want to fork the remote repository first:

```
./repo-manage add -f -p <local_path_to_folder> <repo_url>
```

In the latter case, the remote repository will be forked into your Github account before adding it as a git subtree here. This is useful if intend to make some changes to the role (which you might potentially send upstream via pull requests).

As for the local path, I'd advise to choose a sensible path for the repository to help organizing potentially many roles (e.g. install php -> languages/php/<role_name>, or install docker -> services/containers/docker/<role_name>). It's easiest to choose the role name as it is in Ansible galaxy (author.role_name), so `freckles` can find it easily.


