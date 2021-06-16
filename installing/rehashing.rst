*********
Rehashing
*********

The primary way of configuring Ergo is by modifying the configuration
file. Most changes to the configuration file can be applied at runtime
by "rehashing", i.e., reloading the configuration file without
restarting the server process. This has the advantage of not
disconnecting users. There are two ways to rehash Ergo:

#. If you are an operator with the ``rehash`` capability, you can issue
   the ``/REHASH`` command (you may have to ``/quote rehash``, depending
   on your client)
#. You can send the ``SIGHUP`` signal to Ergo, e.g., via
   ``killall -HUP ergo``

Rehashing also reloads TLS certificates and the MOTD. Some configuration
settings cannot be altered by rehash. You can monitor either the
response to the ``/REHASH`` command, or the server logs, to see if your
rehash was successful.