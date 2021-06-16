*******
Windows
*******

To get started with Ergo on Windows:

#. Make sure you have the `latest
   release <https://github.com/ergochat/ergo/releases/latest>`__
   downloaded.
#. Extract the zip file to a folder.
#. Copy and rename ``default.yaml`` to ``ircd.yaml``.
#. Open up ``ircd.yaml`` using any text editor, and then save it once
   you're happy.
#. Open up a ``cmd.exe`` window, then ``cd`` to where you have Ergo
   extracted.
#. Run ``ergo mkcerts`` if you want to generate new self-signed SSL/TLS
   certificates (note that you can't enable STS if you use self-signed
   certs).

To start the server, type ``ergo run`` and hit enter, and the server
should start!