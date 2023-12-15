|LS| Classification
======================================================================

Labels are a good way to communicate information such as the names of
individual places, but they can't be used for everything.
For example, let us say that someone wants to know what each
``landuse`` area is used for.
Using labels, you would get this:

.. figure:: img/bad_landuse_labels.png
   :align: center

This makes the map's labeling difficult to read and even overwhelming
if there are numerous different landuse areas on the map.

**The goal for this lesson:** To learn how to classify vector data
effectively.

|basic| |FA| Classifying Nominal Data
----------------------------------------------------------------------

#. Open the :guilabel:`Layer Properties` dialog for the ``landuse``
   layer
#. Go to the :guilabel:`Symbology` tab
#. Click on the dropdown that says :guilabel:`Single Symbol` and
   change it to :guilabel:`Categorized`:

   .. figure:: img/categorised_styles.png
      :align: center

#. In the new panel, change the :guilabel:`Value` to ``landuse`` and
   the :guilabel:`Color ramp` to :guilabel:`Random colors`
#. Click the button labeled :guilabel:`Classify`

   .. figure:: img/categorised_style_settings.png
      :align: center

#. Click :guilabel:`OK`

   You'll see something like this:

   .. figure:: img/categorisation_result.png
      :align: center

#. Click the arrow (or plus sign) next to ``landuse`` in the
   :guilabel:`Layers` panel, you'll see the categories explained:

   .. figure:: img/categories_explained.png
      :align: center

   Now our landuse polygons are colored and are classified so that
   areas with the same land use are the same color.

#. If you wish to, you can change the symbol of each landuse
   area by double-clicking the relevant color block in the
   :guilabel:`Layers` panel or in the :guilabel:`Layer Properties`
   dialog:

   .. figure:: img/change_layer_color.png
      :align: center

Notice that there is one category that's empty:

.. figure:: img/empty_category.png
   :align: center

This empty category is used to color any objects which do not have a
landuse value defined or which have a *NULL* value.
It can be useful to keep this empty category so that areas with a
*NULL* value are still represented on the map.
You may like to change the color to more obviously represent a blank
or *NULL* value.

Remember to save your map now so that you don't lose all your
hard-earned changes!

|basic| |TY| More Classification
----------------------------------------------------------------------

Use the knowledge you gained above to classify the ``buildings`` layer.
Set the categorisation against the ``building`` field and use the
:guilabel:`Spectral` color ramp.

.. note:: Remember to zoom into an urban area to see the results.

|IC|
----------------------------------------------------------------------

Symbology allows us to represent the attributes of a layer in an
easy-to-read way.
It allows us as well as the map reader to understand the significance
of features, using any relevant attributes that we choose.
Depending on the problems you face, you'll apply different
classification techniques to solve them.

|WN|
----------------------------------------------------------------------

Now we have a nice-looking map, but how are we going to get it out of
QGIS and into a format we can print out, or make into an image or PDF? That's the topic of the next lesson!


.. Substitutions definitions - AVOID EDITING PAST THIS LINE
   This will be automatically updated by the find_set_subst.py script.
   If you need to create a new substitution manually,
   please add it also to the substitutions.txt file in the
   source folder.

.. |FA| replace:: Follow Along:
.. |IC| replace:: In Conclusion
.. |LS| replace:: Lesson:
.. |TY| replace:: Try Yourself
.. |WN| replace:: What's Next?
.. |basic| image:: /static/common/basic.png
.. |calculateField| image:: /static/common/mActionCalculateField.png
   :width: 1.5em
.. |checkbox| image:: /static/common/checkbox.png
   :width: 1.3em
.. |equalCount| image:: /static/common/mClassificationEqualCount.png
   :width: 1.5em
.. |expression| image:: /static/common/mIconExpression.png
   :width: 1.5em
.. |hard| image:: /static/common/hard.png
.. |majorUrbanName| replace:: Swellendam
.. |moderate| image:: /static/common/moderate.png
.. |newAttribute| image:: /static/common/mActionNewAttribute.png
   :width: 1.5em
.. |radioButtonOn| image:: /static/common/radiobuttonon.png
   :width: 1.5em
.. |saveEdits| image:: /static/common/mActionSaveEdits.png
   :width: 1.5em
.. |symbologyAdd| image:: /static/common/symbologyAdd.png
   :width: 1.5em
.. |symbologyRemove| image:: /static/common/symbologyRemove.png
   :width: 1.5em
.. |toggleEditing| image:: /static/common/mActionToggleEditing.png
   :width: 1.5em
