|LS| Symbology
===============================================================================

The symbology of a layer is its visual appearance on the map.
The basic strength of GIS over other ways of representing data with spatial
aspects is that with GIS, you have a dynamic visual representation of the data
you're working with.

Therefore, the visual appearance of the map (which depends on the symbology of
the individual layers) is very important. The end user of the maps you produce
will need to be able to easily see what the map represents. Equally as
important, you need to be able to explore the data as you're working with it,
and good symbology helps a lot.

In other words, having proper symbology is not a luxury or just nice to have.
In fact, it's essential for you to use a GIS properly and produce maps and
information that people will be able to use.

**The goal for this lesson:** To be able to create any symbology you want for
any vector layer.

|basic| |FA| Changing Colors
-------------------------------------------------------------------------------

To change a layer's symbology, open its :guilabel:`Layer Properties`. Let's
begin by changing the color of the :guilabel:`landuse` layer.

#. Right-click on the :guilabel:`landuse` layer in the layers list.
#. Select the menu item :guilabel:`Properties...` in the menu that appears.

   .. note:: By default, you can also access a layer's properties by
     double-clicking on the layer in the Layers list.

   .. tip:: The |symbology| button at the top of the :guilabel:`Layers`
     panel will open the :guilabel:`Layer Styling` panel. You can use this
     panel to change some properties of the layer: by default, changes will be
     applied immediately!

#. In the :guilabel:`Layer Properties` window, select the |symbology|
   :guilabel:`Symbology` tab:

   .. figure:: img/layer_properties_style.png
      :align: center

#. Click the color select button next to the :guilabel:`Color` label.
   A standard color dialog will appear.
#. Choose a gray color and click :guilabel:`OK`.
#. Click :guilabel:`OK` again in the :guilabel:`Layer Properties` window, and
   you will see the color change being applied to the layer.

|basic| |TY|
-------------------------------------------------------------------------------

Change the color of the :guilabel:`water` layer to light blue. Try to use the
:guilabel:`Layer Styling` panel instead of the :guilabel:`Layer Properties` menu.

.. admonition:: Solution
   :class: dropdown

   * Verify that the colors are changing as you expect them to change.
   * It is enough to select the :guilabel:`water` layer in the legend and then click
     on the |symbology| :sup:`Open the Layer Styling panel` button. Change the color
     to one that fits the water layer.

   .. figure:: img/answer_water_blue.png
      :align: center

   If you want to work on only one layer at a time and don't want the
   other layers to distract you, you can hide a layer by clicking in the checkbox
   next to its name in the layers list. If the box is blank, then the layer
   is hidden.


|basic| |FA| Changing Symbol Structure
-------------------------------------------------------------------------------

This is good stuff so far, but there's more to a layer's symbology than just
its color. Next we want to eliminate the lines between the different land use
areas so as to make the map less visually cluttered.

#. Open the :guilabel:`Layer Properties` window for the :guilabel:`landuse`
   layer.

   Under the |symbology| :guilabel:`Symbology` tab, you will see the same kind
   of dialog as before. This time, however, you're doing more than just quickly
   changing the color.
#. In the symbol layers tree, expand the :guilabel:`Fill` dropdown
   and select the :guilabel:`Simple fill` option.
#. Click on the :guilabel:`Stroke style` dropdown. At the moment, it should be
   showing a short line and the words :guilabel:`Solid Line`.
#. Change this to :guilabel:`No Pen`.

   .. figure:: img/simple_fill_selected.png
      :align: center

#. Click :guilabel:`OK`.

Now the :guilabel:`landuse` layer won't have any lines between areas.


|basic| |TY|
-------------------------------------------------------------------------------

* Change the :guilabel:`water` layer's symbology again so that it has a
  darker blue outline.
* Change the :guilabel:`rivers` layer's symbology to a sensible representation
  of waterways.

Remember: you can use the |symbology| :sup:`Open the Layer Styling panel`
button and see all the changes instantly. That panel also allows you to undo
individual changes while symbolizing a layer.

.. admonition:: Answer
   :class: dropdown

   Your map should now look like this:

   .. figure:: img/answer_symbology1.png
      :align: center

   If you are a Beginner-level user, you may stop here.

   * Use the method above to change the colors and styles for all the remaining
     layers.
   * Try using natural colors for the objects. For example, a road should not be
     red or blue, but can be gray or black.
   * Also feel free to experiment with different :guilabel:`Fill style` and
     :guilabel:`Stroke style` settings for the polygons.

   .. figure:: img/answer_symbology2.png
      :align: center


|moderate| |FA| Scale-Based Visibility
-------------------------------------------------------------------------------

Sometimes you will find that a layer is not suitable for a given scale. For
example, a dataset of all the continents may have low detail, and not be very
accurate at street level. When that happens, you want to be able to hide the
dataset at inappropriate scales.

In our case, we may decide to hide the buildings from view at small scales. This
map, for example...

.. figure:: img/buildings_small_scale.png
   :align: center

... is not very useful. The buildings are hard to distinguish at that scale.

To enable scale-based rendering:

#. Open the :guilabel:`Layer Properties` dialog for the :guilabel:`buildings`
   layer.
#. Activate the |rendering| :guilabel:`Rendering` tab.
#. Enable scale-based rendering by clicking on the checkbox labeled
   :guilabel:`Scale dependent visibility`:
#. Change the :guilabel:`Minimum` value to ``1:10000``.

   .. figure:: img/scale_dependent_visibility.png
      :align: center

#. Click :guilabel:`OK`.

Test the effects of this by zooming in and out in your map, noting when the
:guilabel:`buildings` layer disappears and reappears.

.. note::  You can use your mouse wheel to zoom in increments.
   Alternatively, use the zoom tools to zoom to a window:

   |zoomIn| |zoomOut|

|moderate| |FA| Adding Symbol Layers
-------------------------------------------------------------------------------

Now that you know how to change simple symbology for layers, the next step is
to create more complex symbology. QGIS allows you to do this using symbol
layers.

#. Go back to the :guilabel:`landuse` layer's symbol properties panel (by clicking
   :guilabel:`Simple fill` in the symbol layers tree).

   In this example, the current symbol has no outline (i.e., it uses the
   :guilabel:`No Pen` border style).

   .. figure:: img/simple_fill_selected.png
      :align: center

#. Select the :guilabel:`Fill` level in the tree and click
   the |symbologyAdd| :sup:`Add symbol layer` button.
   The dialog will change to look something like this, with a new symbol layer
   added:

   .. figure:: img/new_symbol_layer.png
      :align: center

   It may appear somewhat different in color, for example, but you're going
   to change that anyway.

Now there's a second symbol layer. Being a solid color, it will of course
completely hide the previous kind of symbol. Plus, it has a :guilabel:`Solid
Line` border style, which we don't want. Clearly this symbol has to be changed.

.. note::  It's important not to get confused between a map layer and a symbol
   layer. A map layer is a vector (or raster) that has been loaded into the
   map. A symbol layer is part of the symbol used to represent a map layer.
   This course will usually refer to a map layer as just a layer, but a symbol
   layer will always be called a symbol layer, to prevent confusion.

With the new :guilabel:`Simple Fill` symbol layer selected:

#. Set the border style to :guilabel:`No Pen`, as before.
#. Change the fill style to something other than :guilabel:`Solid` or
   :guilabel:`No brush`. For example:

   .. figure:: img/new_fill_settings.png
      :align: center

#. Click :guilabel:`OK`.

Now you can see your results and tweak them as needed.
You can even add multiple extra symbol layers and create a kind of texture for
your layer that way.

.. figure:: img/multiple_symbol_layers.png
   :align: center

It's fun! But it probably has too many colors to use in a real map...

|IC|
-------------------------------------------------------------------------------

Changing the symbology for the different layers has transformed a collection of
vector files into a legible map. Not only can you see what's happening, it's
even nice to look at!

|FR|
-------------------------------------------------------------------------------

`Examples of Beautiful Maps
<https://gis.stackexchange.com/questions/3083/seeking-examples-of-beautiful-maps>`_

|WN|
-------------------------------------------------------------------------------

Changing symbols for whole layers is useful, but the information contained
within each layer is not yet available to someone reading these maps. What are
the streets called? Which administrative regions do certain areas belong to?
What are the relative surface areas of the farms? All of this information is
still hidden. The next lesson will explain how to represent this data on your
map.

.. note::  Did you remember to save your map recently?


.. Substitutions definitions - AVOID EDITING PAST THIS LINE
   This will be automatically updated by the find_set_subst.py script.
   If you need to create a new substitution manually,
   please add it also to the substitutions.txt file in the
   source folder.

.. |FA| replace:: Siga o Passo a Passo:
.. |FR| replace:: Leitura Adicional
.. |IC| replace:: Em Conclusão
.. |LS| replace:: Lição:
.. |TY| replace:: Tente Você Mesmo
.. |WN| replace:: O Que Vem a Seguir?
.. |arrowDown| image:: /static/common/mActionArrowDown.png
   :width: 1.5em
.. |basic| image:: /static/common/basic.png
.. |checkbox| image:: /static/common/checkbox.png
   :width: 1.3em
.. |hard| image:: /static/common/hard.png
.. |majorUrbanName| replace:: Swellendam
.. |moderate| image:: /static/common/moderate.png
.. |rendering| image:: /static/common/rendering.png
   :width: 1.5em
.. |symbology| image:: /static/common/symbology.png
   :width: 2em
.. |symbologyAdd| image:: /static/common/symbologyAdd.png
   :width: 1.5em
.. |zoomIn| image:: /static/common/mActionZoomIn.png
   :width: 1.5em
.. |zoomOut| image:: /static/common/mActionZoomOut.png
   :width: 1.5em
