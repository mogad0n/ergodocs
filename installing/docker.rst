******
Docker
******

#. Pull the latest version of Ergo:
   ``docker pull oragono/oragono:latest``
#. Create a volume for persistent data:
   ``docker volume create oragono-data``
#. Run the container, exposing the default ports:
   ``docker run -d --name oragono -v oragono-data:/ircd-data -p 6667:6667 -p 6697:6697 oragono/oragono:latest``

For further information and a sample docker-compose file see the
separate `Docker
documentation <https://github.com/oragono/oragono/blob/master/distrib/docker/README.md>`__.