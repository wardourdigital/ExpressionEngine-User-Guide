#######################
Version Notes for 5.0.0
#######################

.. contents::
   :local:
   :depth: 1

=========================================
Developers: Site config has its own table
=========================================

We've moved all site config values out of the ``exp_sites`` table, and dropped the ``site_*_preferences`` columns. If you have been directly manipulating those columns you will need to update your code and use the Config model instead. For instance, if you wanted to disable comments for site 1 you'd do::

    $config = ee('Model')->get('Config')
      ->filter('site_id', 1)
      ->filter('key', 'enable_comments')
      ->first();

    $config->value = 'n';
    $config->save();
