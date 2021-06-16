**********************************
Upgrading to a new version of Ergo
**********************************

As long as you are using official releases or release candidates of
Ergo, any backwards-incompatible changes should be described in the
changelog.

In general, the config file format should be fully backwards and
forwards compatible. Unless otherwise noted, no config file changes
should be necessary when upgrading Ergo. However, the "config changes"
section of the changelog will typically describe new sections that can
be added to your config to enable new functionality, as well as changes
in the recommended values of certain fields.

The database is versioned; upgrades that involve incompatible changes to
the database require updating the database. If you have
``datastore.autoupgrade`` enabled in your config, the database will be
backed up and upgraded when you restart your server when required.
Otherwise, you can apply upgrades manually:

#. Stop your server
#. Make a backup of your database file
#. Run ``ergo upgradedb`` (from the same working directory and with the
   same arguments that you would use when running ``ergo run``)
#. Start the server again

If you want to run our master branch as opposed to our releases, come
find us in our channel and we can guide you around any potential
pitfalls.