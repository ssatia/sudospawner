# SudoSpawner

Enables [JupyterHub](https://github.com/jupyter/jupyterhub) to run without being root,
by spawning an intermediate process via `sudo`, which takes actions on behalf of the user.

The sudospawner mediator can only do two things:

1. signal processes via os.kill
2. spawn single-user servers

The only thing the Hub user needs sudo access for is launching the sudospawner script itself.

## setup

Install:

    pip install -e .

[Add sudo access to the script](https://github.com/jupyter/jupyterhub/wiki/Using-sudo-to-run-the-server-as-non-root).

Tell JupyterHub to use SudoSpawner, by adding the following to your `jupyterhub_config.py`:

    c.JupyterHubApp.spawner_class='sudospawner.SudoSpawner'

