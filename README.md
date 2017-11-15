# Curated list of Ansible roles, frecklecutables and freckelize adapters

This repository contains a collection of [Ansible roles](http://ansible-docs.readthedocs.io/zh/stable-2.0/rst/playbooks_roles.html), [frecklecutables](https://docs.freckles.io/en/latest/frecklecute_command.html#frecklecutables) and [freckelize adapters](https://docs.freckles.io/en/latest/freckelize_command.html#adapters-profiles) which can be considered useful for a wider audience.

It is assembled using the [`git subtree` command](https://www.atlassian.com/blog/git/alternatives-to-git-submodule-git-subtree), which is why whoever contributes to this repository should try to avoid mixing commits that relate to several different (remote) git repositories.

To make adding and updating new remote subtree repositories containing Ansible roles easier, this repository contains a helper script called 'repo-manage':

## `repo-manage`

### Usage:

#### Adding new remote role

```
./repo-manage add -p <local_path_to_folder> <repo_url>
```

Or, if you want to fork the remote repository first:

```
./repo-manage add -f -p <local_path_to_folder> <repo_url>
```

In the latter case, the remote repository will be forked into your Github account before adding it as a git subtree here. This is useful if intend to make some changes to the role (which you might potentially send upstream via pull requests).

As for the local path, I'd advise to choose a sensible path for the repository to help organizing potentially many roles (e.g. install php -> languages/php/<role_name>, or install docker -> services/containers/docker/<role_name>). It's easiest to choose the role name as it is in Ansible galaxy (author.role_name), so `freckles` can find it easily.

##### Example: Adding the `geerlingguy.docker` role:

```
./repo-manage add -p services/containers/docker/geerlingguy.docker https://github.com/geerlingguy/ansible-role-docker.git                                      
https://github.com/geerlingguy/ansible-role-docker.git
Updating geerlingguy_docker_upstream
warning: no common commits
remote: Counting objects: 151, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 151 (delta 0), reused 0 (delta 0), pack-reused 149
Receiving objects: 100% (151/151), 22.66 KiB | 227.00 KiB/s, done.
Resolving deltas: 100% (68/68), done.
From https://github.com/geerlingguy/ansible-role-docker
 * [new branch]      master     -> geerlingguy_docker_upstream/master
 * [new tag]         1.0.0      -> 1.0.0
 * [new tag]         1.1.0      -> 1.1.0
 * [new tag]         1.2.0      -> 1.2.0
 * [new tag]         2.0.0      -> 2.0.0
 * [new tag]         2.0.1      -> 2.0.1
 * [new tag]         2.0.2      -> 2.0.2
 * [new tag]         2.0.3      -> 2.0.3
 * [new tag]         2.0.4      -> 2.0.4
 * [new tag]         2.0.5      -> 2.0.5
 * [new tag]         2.1.0      -> 2.1.0
git fetch geerlingguy_docker_upstream master
From https://github.com/geerlingguy/ansible-role-docker
 * branch            master     -> FETCH_HEAD
Added dir 'services/containers/docker/geerlingguy.docker'
Added repositury 'https://github.com/geerlingguy/ansible-role-docker.git' (using alias 'geerlingguy_docker_upstream' at path: services/containers/docker/geerlingguy.docker
[master a3c7987] Added remote role repo 'https://github.com/geerlingguy/ansible-role-docker.git' (alias: geerlingguy_docker_upstream)to path: services/containers/docker/geerlingguy.docker
 1 file changed, 1 insertion(+)
 create mode 100644 .role_repos
```



#### Updating remote role

```
./repo-manage pull-upstream <role_name>
```

##### Example: pulling updates from the upstream `geerlingguy.docker` role

```
./repo-manage pull-upstream geerlingguy.docker
```
