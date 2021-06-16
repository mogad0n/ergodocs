********************
Becoming an operator
********************

Many administrative actions on an IRC server are performed "in-band" as
IRC commands sent from a client. The client in question must be an IRC
operator ("oper", "ircop"). The easiest way to become an operator on
your new Ergo instance is first to pick a strong, secure password, then
"hash" it using the ``ergo genpasswd`` command (run ``ergo genpasswd``
from the command line, then enter your password twice), then copy the
resulting hash into the ``opers`` section of your ``ircd.yaml`` file.
Then you can become an operator by issuing the IRC command:
``/oper admin mysecretpassword``.