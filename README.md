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

* ``mlnx_ufm_action``: Action to perform. One of ``deploy``, ``destroy``,
  ``pull``, ``reconfigure``, ``upgrade``. Defaults to ``deploy``.
* ``mlnx_ufm_enabled``: Whether UFM is enabled. Defaults to ``true``.
* ``mlnx_ufm_image``: Docker image name. Required.
* ``mlnx_ufm_tag``: Docker image tag. Defaults to ``latest``.
* ``mlnx_ufm_image_full``: Full docker image specification.
* ``mlnx_ufm_restart_policy``: Docker restart policy for the UFM container.
  Defaults to ``unless-stopped``.
* ``mlnx_ufm_restart_retries``: Number of Docker restarts. Defaults to 10.
* ``mlnx_ufm_licenses_path``: Path to a directory on the host containing
  Mellanox UFM licenses. Default is ``/etc/mlnx-ufm/licenses``.

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
