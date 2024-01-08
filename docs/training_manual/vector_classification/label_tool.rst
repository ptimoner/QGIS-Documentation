|LS| Labels
===============================================================================

Labels can be added to a map to show any information about an object. Any
vector layer can have labels associated with it. These labels rely on the
attribute data of a layer for their content.

**The goal for this lesson:** To apply useful and good-looking labels to a
layer.


|basic| |FA| Using Labels
-------------------------------------------------------------------------------

First, ensure that the |labelingSingle| button is visible in the GUI:

#. Go to the menu item :menuselection:`View --> Toolbars`
#. Ensure that the :guilabel:`Label Toolbar` item has a check mark next to it.
   If it doesn't, click on the :guilabel:`Label Toolbar` item to activate it.
#. Click on the ``places`` layer in the :guilabel:`Layers` panel so that
   it is highlighted
#. Click on the |labelingSingle| toolbar button to open the
   :guilabel:`Labels` tab of the :guilabel:`Layer Styling` panel

#. Switch from :guilabel:`No Labels` to |labelingSingle| :guilabel:`Single Labels`

   You'll need to choose which field in the attributes will be used for the
   labels. In the previous lesson, you decided that the ``name`` field was the
   most suitable one for this purpose.

#. Select ``name`` from the Value list:

   .. figure:: img/select_label_with.png
      :align: center

#. Click :guilabel:`Apply`

The map should now have labels like this:

.. figure:: img/first_place_names.png
   :align: center


|basic| |FA| Changing Label Options
-------------------------------------------------------------------------------

Depending on the styles you chose for your map in earlier lessons, you might
find that the labels are not appropriately formatted and either overlap or
are too far away from their point markers.

.. note::  Above, you used the |labelingSingle| button in the
   :guilabel:`Label Toolbar` to open the :guilabel:`Layer Styling` panel. As
   with :guilabel:`Symbology`, the same label options are available via both
   the :guilabel:`Layer Styling` panel and the :guilabel:`Layer Properties`
   dialog. Here, you'll use the :guilabel:`Layer Properties` dialog.

#. Open the :guilabel:`Layer Properties` dialog by double-clicking on the
   ``places`` layer
#. Select the |labelingSingle| :guilabel:`Labels` tab
#. Make sure :guilabel:`Text` is selected in the left-hand options list, then
   update the text formatting options to match those shown here:

   .. figure:: img/label_formatting_options.png
      :align: center

#. Click :guilabel:`Apply`

   That font may be larger and more familiar to users, but its readability is
   still dependent on what layers are rendered beneath it. To solve this,
   let's take a look at the :guilabel:`Buffer` option.

#. Select :guilabel:`Buffer` from the left-hand options list
#. Select the checkbox next to :guilabel:`Draw text buffer`, then choose
   options to match those shown here:

   .. figure:: img/buffer_options.png
      :align: center

#. Click :guilabel:`Apply`

   You'll see that this adds a colored buffer or border to the place labels,
   making them easier to pick out on the map:

   .. figure:: img/buffer_results.png
      :align: center

   Now we can address the positioning of the labels in relation to their point
   markers.

#. Select :guilabel:`Placement` from the left-hand options list
#. Select :guilabel:`Around point` and change the value of
   :guilabel:`Distance` to ``2.0`` Millimeters:

   .. figure:: img/offset_placement_settings.png
      :align: center

#. Click :guilabel:`Apply`

   You'll see that the labels are no longer overlapping their point markers.


|IC|
-------------------------------------------------------------------------------

You've learned how to use layer attributes to create dynamic labels. This can
make your map a lot more informative and stylish!


|WN|
-------------------------------------------------------------------------------

Now that you know how attributes can make a visual difference for your map, how
about using them to change the symbology of objects themselves? That's the
topic for the next lesson!


.. Substitutions definitions - AVOID EDITING PAST THIS LINE
   This will be automatically updated by the find_set_subst.py script.
   If you need to create a new substitution manually,
   please add it also to the substitutions.txt file in the
   source folder.

.. |FA| replace:: Siga o Passo a Passo:
.. |IC| replace:: Em Conclusão
.. |LS| replace:: Lição:
.. |TY| replace:: Tente Você Mesmo
.. |WN| replace:: O Que Vem a Seguir?
.. |basic| image:: /static/common/basic.png
.. |changeLabelProperties| image:: /static/common/mActionChangeLabelProperties.png
   :width: 1.5em
.. |dataDefine| image:: /static/common/mIconDataDefine.png
   :width: 1.5em
.. |hard| image:: /static/common/hard.png
.. |labelingSingle| image:: /static/common/labelingSingle.png
   :width: 1.5em
.. |majorUrbanName| replace:: Swellendam
.. |moderate| image:: /static/common/moderate.png
.. |moveLabel| image:: /static/common/mActionMoveLabel.png
   :width: 1.5em
.. |newAttribute| image:: /static/common/mActionNewAttribute.png
   :width: 1.5em
.. |openTable| image:: /static/common/mActionOpenTable.png
   :width: 1.5em
.. |pinLabels| image:: /static/common/mActionPinLabels.png
   :width: 1.5em
.. |rotateLabel| image:: /static/common/mActionRotateLabel.png
   :width: 1.5em
.. |showHideLabels| image:: /static/common/mActionShowHideLabels.png
   :width: 1.5em
.. |showPinnedLabels| image:: /static/common/mActionShowPinnedLabels.png
   :width: 1.5em
.. |showUnplacedLabel| image:: /static/common/mActionShowUnplacedLabel.png
   :width: 1.5em
.. |toggleEditing| image:: /static/common/mActionToggleEditing.png
   :width: 1.5em
