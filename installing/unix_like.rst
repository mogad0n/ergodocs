****************************
macOS / Linux / Raspberry Pi
****************************

To get started with Ergo on macOS, Linux, or on a Raspberry Pi:

#. Make sure you have the `latest
   release <https://github.com/ergochat/ergo/releases/latest>`__ for
   your OS/distro downloaded.
#. Extract the tar.gz file to a folder.
#. Copy and rename ``default.yaml`` to ``ircd.yaml``.
#. Open up ``ircd.yaml`` using any text editor, and then save it once
   you're happy.
#. Open up a Terminal window, then ``cd`` to where you have Ergo
   extracted.
#. Run ``./ergo mkcerts`` if you want to generate new self-signed
   SSL/TLS certificates (note that you can't enable STS if you use
   self-signed certs).

To start the server, type ``./ergo run`` and hit enter, and the server
should be ready to use!