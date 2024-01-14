|LS| Useful QGIS Plugins
===============================================================================

Now that you can install, enable and disable plugins, let's see how this can
help you in practice by looking at some examples of useful plugins.

**The goal for this lesson:** To familiarize yourself with the plugin interface
and get acquainted with some useful plugins.


|basic| |FA| The QuickMapServices Plugin
-------------------------------------------------------------------------------

The QuickMapServices plugin is a simple and easy to use plugin that adds base maps
to your QGIS project.
It has many different options and settings.
Let's start to explore some of its features.

#. Start a new map and add the :guilabel:`roads` layer from the :file:`training_data`
   Geopackage.
#. Install the **QuickMapServices** plugin.
#. Click on :menuselection:`Web --> QuickMapServices`.
   The first menu lists different map providers (``OSM``, ``NASA``) with available maps.
#. Click on an entry and you would load the base map into your project.

   .. figure:: img/qms_result.png
      :align: center
      :width: 80%

Nice! But one of the main strengths of QMS is to provide access to many data providers.
Let's add them.

#. Click on :menuselection:`Web --> QuickMapServices --> Settings`
#. Go to the :guilabel:`More services` tab.
#. Read carefully the message of this tab and if you agree click on the
   :guilabel:`Get Contributed pack` button.
#. Click :guilabel:`Save`.

#. Reopen the :menuselection:`Web --> QuickMapServices` menu you will see
   that more providers are available.

   .. figure:: img/qms_menu.png
      :align: center

#. Choose the one that best fits your needs, and load the data in the project!

It is also possible to search trough the now available data providers

#. Open the plugin's search tab by clicking on :menuselection:`Web --> QuickMapServices --> Search QMS`.
   This option of the plugin allows you to filter the available base maps
   by the current extent of the map canvas or using a search word.
#. Click on the :guilabel:`Filter by extent` and you should see one service available.
   If no service is found, zoom out and pan around the world (or your location)
   or search with a keyword.
#. Click on the :guilabel:`Add` button next to a returned dataset to load it.
#. The base map will be loaded and you will have a background for the map.

   .. figure:: img/qms_search_added.png
      :align: center
      :width: 80%


|basic| |FA| The QuickOSM Plugin
-------------------------------------------------------------------------------

With an incredible simple interface, the QuickOSM plugin allows you to download
`OpenStreetMap <https://www.openstreetmap.org/>`_ data.

#. Start a new empty project and add the :guilabel:`roads` layer from the
   :file:`training_data` GeoPackage.
#. Install the **QuickOSM** plugin.
   The plugin adds two new buttons in the QGIS Toolbar
   and is accessible in the :menuselection:`Vector --> QuickOSM` menu.
#. Open the QuickOSM dialog. The plugin has many different tabs: we will use the
   :guilabel:`Quick Query` one.
#. You can download specific features by selecting a generic :guilabel:`Key` or be more
   specific and choose a specific :guilabel:`Key` and :guilabel:`Value` pair.

   .. tip:: if you are not familiar with the :guilabel:`Key` and :guilabel:`Value`
    system, click on the :guilabel:`Help with key/value` button. It will open a
    web page with a complete description of this concept of OpenStreetMap.

#. Look for :guilabel:`railway` in the :guilabel:`Key` menu and let the :guilabel:`Value` be
   empty: so we are downloading all the :guilabel:`railway` features without specifying
   any values.
#. Select :guilabel:`Layer Extent` in the next drop-down menu and choose :guilabel:`roads`.
#. Click on the :guilabel:`Run query` button.

   .. figure:: img/quickosm_setup.png
      :align: center

After some seconds the plugin will download all the features tagged in OpenStreetMap
as ``railway`` and load them directly into the map.

Nothing more! All the layers are loaded in the legend and are shown in the map
canvas.

.. figure:: img/quickosm_result.png
   :align: center
   :width: 60 %

.. warning:: QuickOSM creates temporary layer when downloading the data. If you
  want to save them permanently, click on the |indicatorMemory| icon next to the
  layer and choose the options you prefer. Alternatively you can open the
  :kbd:`Advanced` menu in QuickOSM and choose where to save the data in the
  :guilabel:`Directory` menu.


|IC|
-------------------------------------------------------------------------------

There are many useful plugins available for QGIS. Using the built-in tools for
installing and managing these plugins, you can find new plugins and make
optimum use of them.

.. Substitutions definitions - AVOID EDITING PAST THIS LINE
   This will be automatically updated by the find_set_subst.py script.
   If you need to create a new substitution manually,
   please add it also to the substitutions.txt file in the
   source folder.

.. |FA| replace:: Follow Along:
.. |IC| replace:: In Conclusion
.. |LS| replace:: Lesson:
.. |WN| replace:: What's Next?
.. |addHtml| image:: /static/common/mActionAddHtml.png
   :width: 1.5em
.. |basic| image:: /static/common/basic.png
.. |hard| image:: /static/common/hard.png
.. |helpContents| image:: /static/common/mActionHelpContents.png
   :width: 1.5em
.. |indicatorMemory| image:: /static/common/mIndicatorMemory.png
   :width: 1.5em
.. |saveMapAsImage| image:: /static/common/mActionSaveMapAsImage.png
   :width: 1.5em
.. |symbology| image:: /static/common/symbology.png
   :width: 2em
