Memcached for Ubuntu
~~~~~~~~~~~~~~~~~~~~

The Identity service authentication mechanism for services uses Memcached
to cache tokens. The memcached service typically runs on the controller
node. For production deployments, we recommend enabling a combination of
firewalling, authentication, and encryption to secure it.

Install and configure components
--------------------------------

#. Install the packages:

For Ubuntu versions prior to 18.04 use:

   .. code-block:: console

      # apt install memcached python-memcache

For Ubuntu 18.04 and newer versions use:

   .. code-block:: console

      # apt install memcached python3-memcache

2. Edit the ``/etc/memcached.conf`` file and configure the
   service to use the management IP address of the controller node.
   This is to enable access by other nodes via the management network:

   .. code-block:: none

      -l 10.0.0.11

   .. note::

      Change the existing line that had ``-l 127.0.0.1``.

Finalize installation
---------------------

* Restart the Memcached service:

  .. code-block:: console

     # service memcached restart
