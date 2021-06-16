*********************
Environment variables
*********************

Ergo can also be configured using environment variables, using the
following technique:

#. Find the "path" of the config variable you want to override in the
   YAML file, e.g., ``server.websockets.allowed-origins``
#. Convert each path component from "kebab case" to "screaming snake
   case", e.g., ``SERVER``, ``WEBSOCKETS``, and ``ALLOWED_ORIGINS``.
#. Prepend ``ORAGONO`` to the components, then join them all together
   using ``__`` as the separator, e.g.,
   ``ORAGONO__SERVER__WEBSOCKETS__ALLOWED_ORIGINS``.
#. Set the environment variable of this name to a JSON (or YAML) value
   that will be deserialized into this config field, e.g.,
   ``export ORAGONO__SERVER__WEBSOCKETS__ALLOWED_ORIGINS='["https://irc.example.com", "https://chat.example.com"]'``

However, settings that were overridden using this technique cannot be
rehashed --- changing them will require restarting the server.
