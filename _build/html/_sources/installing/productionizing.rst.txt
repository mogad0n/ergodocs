****************************
Productionizing with systemd
****************************

The recommended way to operate ergo as a service on Linux is via
systemd. This provides a standard interface for starting, stopping, and
rehashing (via ``systemctl reload``) the service. It also captures
ergo's loglines (sent to stderr in the default configuration) and writes
them to the system journal.

The only major distribution that currently packages Ergo is Arch Linux;
the aforementioned AUR package includes a systemd unit file. However, it
should be fairly straightforward to set up a productionized Ergo on any
Linux distribution. Here's a quickstart guide for Debian/Ubuntu:

#. Create a dedicated, unprivileged role user who will own the ergo
   process and all its associated files:
   ``adduser --system --group ergo``. This user now has a home directory
   at ``/home/ergo``. To prevent other users from viewing Ergo's
   configuration file, database, and certificates, restrict the
   permissions on the home directory: ``chmod 0700 /home/ergo``.
#. Copy the executable binary ``ergo``, the config file ``ircd.yaml``,
   the database ``ircd.db``, and the self-signed TLS certificate
   (``fullchain.pem`` and ``privkey.pem``) to ``/home/ergo``. (If you
   don't have an ``ircd.db``, it will be auto-created as
   ``/home/ergo/ircd.db`` on first launch.) Ensure that they are all
   owned by the new ergo role user:
   ``sudo chown ergo:ergo /home/ergo/*``. Ensure that the configuration
   file logs to stderr.
#. Install our example
   `ergo.service <https://github.com/ergochat/ergo/blob/master/distrib/systemd/ergo.service>`__
   file to ``/etc/systemd/system/ergo.service``.
#. Enable and start the new service with the following commands:

   #. ``systemctl daemon-reload``
   #. ``systemctl enable ergo.service``
   #. ``systemctl start ergo.service``
   #. Confirm that the service started correctly with
      ``systemctl status ergo.service``

On a non-systemd system, ergo can be configured to log to a file and
used `logrotate(8) <https://linux.die.net/man/8/logrotate>`__, since it
will reopen its log files (as well as rehashing the config file) upon
receiving a SIGHUP. To rehash manually outside the context of log
rotation, you can use ``killall -HUP ergo`` or ``pkill -HUP ergo``.