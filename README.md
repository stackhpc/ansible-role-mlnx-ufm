Mellanox UFM Infiniband Fabric Manager
======================================

This role can be used to configure a Mellanox UFM Infiniband fabric manager
running in a Docker container.

Tooling to build a compatible container image is provided on `Github
<https://github.com/stackhpc/docker-mlnx-ufm>`.

Requirements
------------

The host executing the role has the following requirements:

* Docker engine
* Python ``docker >= 2.0.0``

Role Variables
--------------

* ``mlnx_ufm_action``: Action to perform. One of ``build``, ``deploy``,
  ``destroy``, ``pull``, ``reconfigure``, ``upgrade``. Defaults to ``deploy``.
* ``mlnx_ufm_enabled``: Whether UFM is enabled. Defaults to ``true``.
* ``mlnx_ufm_image``: Docker image name. Required.
* ``mlnx_ufm_tag``: Docker image tag. Defaults to ``latest``.
* ``mlnx_ufm_image_full``: Full docker image specification.
* ``mlnx_ufm_restart_policy``: Docker restart policy for the UFM container.
  Defaults to ``unless-stopped``.
* ``mlnx_ufm_restart_retries``: Number of Docker restarts. Defaults to 10.
* ``mlnx_ufm_startup_config_path``: Path to a script template on localhost
  containing startup configuration. Default is
  ``/etc/mlnx-ufm/mlnx-ufm-configure``.
* ``mlnx_ufm_licenses_path``: Path to a directory on localhost containing
  Mellanox UFM licenses. Default is ``/etc/mlnx-ufm/licenses``.
* ``mlnx_ufm_config_path``: Path to a directory on the remote host to store
  configuration.  Default is ``/etc/mlnx-ufm``.

The following variables are relevant only when ``mlnx_ufm_action`` is
``build``:

* ``mlnx_ufm_repo_url``: URL of the git repo containing the image. Default is
  ``https://github.com/stackhpc/docker-mlnx-ufm``.
* ``mlnx_ufm_repo_version``: Version to check out for the git repo containing
  the image. Default is ``master``.
* ``mlnx_ufm_repo_checkout_path``: Path to a directory in which to check out
  the git repo. Default is ``/tmp``.
* ``mlnx_ufm_version``: Version of the UFM software. This must be set to build
  the image.
* ``mlnx_ufm_tarball_url``: URL of the UFM software tarball. This must be set
  to build the image.
* ``mlnx_ufm_ofed_repo_url``: URL of the OFED package repository. This must be
  set to build the image.
* ``mlnx_ufm_push``: Whether to push images after they have been built. Default
  is ``false``.
* ``mlnx_ufm_force_rebuild``: Whether to build the image even if an image of
  the same name and tag exists. Default is ``false``.

Dependencies
------------

None

Example Playbook
----------------

The following playbook configures Mellanox UFM.

    ---
    - hosts: mlnx-ufm
      roles:
        - role: mlnx-ufm

Author Information
------------------

- Mark Goddard (<mark@stackhpc.com>)
