****************************
Using valid TLS certificates
****************************

The other major hurdle for productionizing (but one well worth the
effort) is obtaining valid TLS certificates for your domain, if you
haven't already done so:

#. The simplest way to get valid TLS certificates is from `Let's
   Encrypt <https://letsencrypt.org/>`__ with
   `Certbot <https://certbot.eff.org/>`__. The correct procedure will
   depend on whether you are already running a web server on port 80. If
   you are, follow the guides on the Certbot website; if you aren't, you
   can use
   ``certbot certonly --standalone --preferred-challenges http -d example.com``
   (replace ``example.com`` with your domain).
#. At this point, you should have certificates available at
   ``/etc/letsencrypt/live/example.com`` (replacing ``example.com`` with
   your domain). You should serve ``fullchain.pem`` as the certificate
   and ``privkey.pem`` as its private key. However, these files are
   owned by root and the private key is not readable by the ergo role
   user, so you won't be able to use them directly in their current
   locations. You can write a post-renewal hook for certbot to make
   copies of these certificates accessible to the ergo role user. For
   example, install the following script as
   ``/etc/letsencrypt/renewal-hooks/post/install-ergo-certificates``,
   again replacing ``example.com`` with your domain name, and chmod it
   0755:

.. code:: bash

    #!/bin/bash

    set -eu

    umask 077
    cp /etc/letsencrypt/live/example.com/fullchain.pem /home/ergo/
    cp /etc/letsencrypt/live/example.com/privkey.pem /home/ergo/
    chown ergo:ergo /home/ergo/*.pem
    # rehash ergo, which will reload the certificates:
    systemctl reload ergo.service

Executing this script manually will install the certificates for the
first time and perform a rehash, enabling them.

If you are using Certbot 0.29.0 or higher, you can also change the
ownership of the files under ``/etc/letsencrypt`` so that the ergo user
can read them, as described in the `UnrealIRCd
documentation <https://www.unrealircd.org/docs/Setting_up_certbot_for_use_with_UnrealIRCd#Tweaking_permissions_on_the_key_file>`__.