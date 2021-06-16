.. Ergo documentation master file, created by
   sphinx-quickstart on Wed Jun 16 02:27:49 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Ergo's documentation!
================================

::

      ___ _ __ __ _  ___  
     / _ \ '__/ _` |/ _ \ 
    |  __/ | | (_| | (_) |
     \___|_|  \__, |\___/ 
               __/ |      
              |___/     


This document goes over the Ergo IRC server, how to get it running and
how to use it once it is up and running!

If you have any suggestions, issues or questions, feel free to submit an
issue on our `GitHub repo <https://github.com/ergochat/ergo>`__ or ask
in our channel ``#ergo`` on
`irc.ergo.chat <ircs://irc.ergo.chat:6697/#ergo>`__ or ``#ergo`` on
`irc.libera.chat <ircs://irc.libera.chat:6697/#ergo>`__.

Project Basics
--------------

Ergo is an ircd written "from scratch" in the
`Go <https://en.wikipedia.org/wiki/Go_%28programming_language%29>`__
language, i.e., it `shares no
code <https://github.com/grawity/irc-docs/blob/master/family-tree.txt>`__
with the original ircd implementation or any other major ircd. It began
as `ergonomadic <https://github.com/jlatt/ergonomadic>`__, which was
developed by Jeremy Latt between 2012 and 2014. In 2016, Daniel Oaks
forked the project under the name Oragono, in order to prototype
`IRCv3 <https://ircv3.net/>`__ features and for use as a reference
implementation of the `Modern IRC
specification <https://modern.ircdocs.horse>`__. Oragono 1.0.0 was
released in February 2019; the project switched to its current name of
Ergo in June 2021.

Ergo's core design goals are:

-  Being simple to set up and use
-  Combining the features of an ircd, a services framework, and a
   bouncer (integrated account management, history storage, and bouncer
   functionality)
-  Bleeding-edge `IRCv3
   support <http://ircv3.net/software/servers.html>`__, suitable for use
   as an IRCv3 reference implementation
-  Highly customizable via a rehashable (i.e., reloadable at runtime)
   YAML config

In addition to its unique features (integrated services and bouncer,
comprehensive internationalization), Ergo also strives for feature
parity with other major servers. Ergo is a mature project with multiple
communities using it as a day-to-day chat server --- we encourage you to
consider it for your organization or community!

Scalability
-----------

We believe Ergo should scale comfortably to 10,000 clients and 2,000
clients per channel, making it suitable for small to medium-sized teams
and communities. Ergo does not currently support server-to-server
linking (federation), meaning that all clients must connect to the same
instance. However, since Ergo is implemented in Go, it is reasonably
effective at distributing work across multiple cores on a single server;
in other words, it should "scale up" rather than "scaling out".
(Horizontal scalability is
`planned <https://github.com/ergochat/ergo/issues/1532>`__ but is not
scheduled for development in the near term.)

Even though it runs as a single instance, Ergo can be deployed for high
availability (i.e., with no single point of failure) using Kubernetes.
This technique uses a k8s
`LoadBalancer <https://kubernetes.io/docs/tasks/access-application-cluster/create-external-load-balancer/>`__
to receive external traffic and a
`Volume <https://kubernetes.io/docs/concepts/storage/volumes/>`__ to
store the embedded database file. See `Hashbang's
implementation <https://github.com/hashbang/gitops/tree/master/ircd>`__
for a "worked example".

If you're interested in deploying Ergo at scale or for high
availability, or want performance tuning advice, come find us on
``#ergo`` on `Libera <ircs://irc.libera.chat:6697/#ergo>`__, we're very
interested in what our software can do!

Contents:

.. toctree::
   :maxdepth: 3
   
   installing/index.rst
   features/index.rst
   faqs/index.rst
   user-guide/index.rst
   irc-over-tls/index.rst
   modes/index.rst
   commands/index.rst
   working-with-other-software/index.rst






Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
