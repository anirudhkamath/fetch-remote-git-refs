# Automated fetching of remote refs

This tool is meant to be used to automatically fetch remote Git refs for the projects you clone or maintain on your system.

## Pre-requisites

- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) must be installed
- [Git](https://git-scm.com/downloads) must be installed (obviously)
- The remotes for your Git projects must be configured with your remote username and password/remote access token. [Create a remote access token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) and make sure the remotes for your projects are of the form

```bash
user> git remote -v
origin  https://{username}:{token}@github.com/project.git (fetch)
origin  https://{username}:{token}@github.com/project.git (push)
```

- Add the root directory to [`git-fetch-remotes.yml`](git-fetch-remotes.yml) to point to where your Git projects are stored- **this requires your projects to be stored in one directory**. Please provide a full path for this variable.

```yaml
vars:
  root_directory: "~"  # this will not work
```

## Running the tool

I usually maintain an alias on my terminal that I call to run the playbook.

```bash
alias xyz="ansible-playbook /path/to/git-fetch-remotes.yml"
```

Place the path to this place in the above `ansible-playbook` command. Then just run the alias:

```bash
user> xyz
PLAY [FETCH REMOTES FOR YOUR REPOS] *****************************************************************************************************************************************************************************

TASK [LIST ALL DIRECTORIES IN ROOT WITH INDICATOR] **************************************************************************************************************************************************************
changed: [localhost]

TASK [LOOP THROUGH LIST OF ITEMS IN ROOT] ***********************************************************************************************************************************************************************

(output omitted)
```

## A run through the playbook

Please find my [blog post](https://anirudhkamath.github.io/network-automation-blog/notes/automated-refs-update.html).
