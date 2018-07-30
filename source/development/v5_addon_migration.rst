v5 Add-on Migration
===================

.. highlight:: javascript

Provided your add-on is compatible ExpressionEngine 4, it's very likely your add-on works unencumbered in ExpressionEngine 5. But here's the gist on what's changed in ExpressionEngine 5, just in case.

What's changed?
---------------

Site config has its own table
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

We've moved all site config values out of the ``exp_sites`` table, and dropped the ``site_*_preferences`` columns. If you have been directly manipulating those columns you will need to update your code and use the Config model instead. For instance, if you wanted to disable comments for site 1 you'd do::

    $config = ee('Model')->get('Config')
      ->filter('site_id', 1)
      ->filter('key', 'enable_comments')
      ->first();

    $config->value = 'n';
    $config->save();

You do not need to change anything to read config values; continue to use ``ee()->config->item(...)``.
