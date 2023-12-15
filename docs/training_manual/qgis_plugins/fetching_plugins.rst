|LS| Installing and Managing Plugins
===============================================================================

To begin using plugins, you need to know how to download, install and activate
them. To do this, you will learn how to use the :guilabel:`Plugin Installer`
and :guilabel:`Plugin Manager`.

**The goal for this lesson:** To understand and use QGIS' plugin system.

|basic| |FA| Managing Plugins
-------------------------------------------------------------------------------

#. To open the :guilabel:`Plugin Manager`, click on the menu item
   :menuselection:`Plugins --> Manage and Install Plugins`.
#. In the dialog that opens, find the :guilabel:`Processing` plugin:

   .. figure:: img/select_processing_plugin.png
      :align: center

#. Click in the box next to this plugin and uncheck it to deactivate it.
#. Click :guilabel:`Close`.
#. Looking at the menu, you will notice that the :guilabel:`Processing` menu is
   is now gone. This means that many of the processing functions you have been
   using before have disappeared! For example look at the :menuselection:`Vector
   -->` and :menuselection:`Raster -->` menus. This is because they are part of
   the :guilabel:`Processing` plugin, which needs to be activated to use them.
#. Open the :guilabel:`Plugin Manager` again and reactivate the
   :guilabel:`Processing` plugin by clicking in the checkbox next to it.
#. :guilabel:`Close` the dialog.
   The :guilabel:`Processing` menu and functions should be available again.


.. _plugin_installation:

|basic| |FA| Installing New Plugins
-------------------------------------------------------------------------------

The list of plugins that you can activate and deactivate draws from the plugins
that you currently have installed. To install new plugins:

#. Select the :guilabel:`Not Installed` option in the :guilabel:`Plugin Manager`
   dialog. The plugins available for you to install will be listed here.
   This list will vary depending on your existing system setup.

   .. figure:: img/get_more_plugins.png
      :align: center

#. Find information about the plugin by selecting it in the list

   .. figure:: img/plugin_details.png
      :align: center

#. Install the one(s) you are interested in by clicking the :guilabel:`Install
   Plugin` button below the plugin information panel.

.. note:: if the plugin has some error it will be listed in the :guilabel:`Invalid`
  tab. You can then contact the plugin owner to fix the problem.


|IC|
-------------------------------------------------------------------------------

Installing plugins in QGIS should be straightforward and effective!

|WN|
-------------------------------------------------------------------------------

Next we'll introduce you to some useful plugins as examples.


.. Substitutions definitions - AVOID EDITING PAST THIS LINE
   This will be automatically updated by the find_set_subst.py script.
   If you need to create a new substitution manually,
   please add it also to the substitutions.txt file in the
   source folder.

.. |FA| replace:: Follow Along:
.. |IC| replace:: In Conclusion
.. |LS| replace:: Lesson:
.. |WN| replace:: What's Next?
.. |basic| image:: /static/common/basic.png
