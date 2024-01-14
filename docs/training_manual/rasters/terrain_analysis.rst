|LS| Terrain Analysis
======================================================================

Certain types of rasters allow you to gain more insight into the
terrain that they represent.
Digital Elevation Models (DEMs) are particularly useful in this
regard.
In this lesson you will use terrain analysis tools to find out more
about the study area for the proposed residential development from
earlier.

**The goal for this lesson:** To use terrain analysis tools to derive
more information about the terrain.

|basic| |FA| Calculating a Hillshade
----------------------------------------------------------------------

We are going to use the same DEM layer as in the previous lesson.
If you are starting this chapter from scratch, use the
:guilabel:`Browser` panel and load the
:file:`raster/SRTM/srtm_41_19.tif`.

The DEM layer shows you the elevation of the terrain, but it can
sometimes seem a little abstract.
It contains all the 3D information about the terrain that you need,
but it doesn't look like a 3D object.
To get a better impression of the terrain, it is possible to calculate
a *hillshade*, which is a raster that maps the terrain using light and
shadow to create a 3D-looking image.

We are going to use algorithms in the
:menuselection:`Raster --> Raster terrain analysis` menu.

#. Click on the :menuselection:`Hillshade` menu
#. The algorithm allows you to specify the position of the light
   source: :guilabel:`Azimuth` has values from 0 (North) through 90
   (East), 180 (South) and 270 (West), while the
   :guilabel:`Vertical angle` sets how high the light source is
   (0 to 90 degrees).
#. We will use the following values:

   * :guilabel:`Z factor` at ``1.0``
   * :guilabel:`Azimuth (horizontal angle)` at ``300.0``\°
   * :guilabel:`Vertical angle` at ``40.0``\°

   .. figure:: img/hillshade_explanation.png
      :align: center

#. Save the file in a new folder :file:`exercise_data/raster_analysis/`
   with the name ``hillshade``
#. Finally click on :guilabel:`Run`

You will now have a new layer called :guilabel:`hillshade` that looks like
this:

.. figure:: img/hillshade_raster.png
   :align: center

That looks nice and 3D, but can we improve on this? On its own, the hillshade
looks like a plaster cast. Can't we use it together with our other, more
colorful rasters somehow? Of course we can, by using the hillshade as an
overlay.

|basic| |FA| Using a Hillshade as an Overlay
----------------------------------------------------------------------

A hillshade can provide very useful information about the sunlight at a given
time of day. But it can also be used for aesthetic purposes, to make the map
look better. The key to this is setting the hillshade to being mostly
transparent.

#. Change the symbology of the original :guilabel:`srtm_41_19` layer to use the
   :guilabel:`Pseudocolor` scheme as in the previous exercise
#. Hide all the layers except the :guilabel:`srtm_41_19` and :guilabel:`hillshade`
   layers
#. Click and drag the :guilabel:`srtm_41_19` to be beneath the :guilabel:`hillshade`
   layer in the :guilabel:`Layers` panel
#. Set the :guilabel:`hillshade` layer to be transparent by clicking on the
   :guilabel:`Transparency` tab in the layer properties
#. Set the :guilabel:`Global opacity` to ``50%``.

   You'll get a result like this:

   .. figure:: img/hillshade_pseudocolor.png
      :align: center

#. Switch the :guilabel:`hillshade` layer off and back on in the
   :guilabel:`Layers` panel to see the difference it makes.

Using a hillshade in this way, it's possible to enhance the topography of the
landscape. If the effect doesn't seem strong enough to you, you can change the
transparency of the :guilabel:`hillshade` layer; but of course, the brighter
the hillshade becomes, the dimmer the colors behind it will be. You will need
to find a balance that works for you.

Remember to save the project when you are done.


|moderate| |FA| Calculating the Slope
----------------------------------------------------------------------

*Slope* informs about how steep the terrain is. If, for example,
you want to build houses on the land there, then you need land
that is relatively flat.

To calculate the slope, you need to use the :menuselection:`Slope` algorithm
of the :menuselection:`Processing --> Raster terrain analysis`.

#. Open the algorithm
#. Choose :guilabel:`srtm_41_19` as the :guilabel:`Elevation layer`
#. Keep the :guilabel:`Z factor` at ``1.0``
#. Save the output as a file with the name ``slope`` in the same folder as the
   ``hillshade``
#. Click on :guilabel:`Run`

Now you'll see the slope of the terrain, each pixel holding the corresponding
slope value. Black pixels show flat terrain and white pixels, steep terrain:

.. figure:: img/slope_raster.png
   :align: center


|moderate| |TY| Calculating the aspect
----------------------------------------------------------------------

*Aspect* is the compass direction that the slope of the terrain faces. An aspect
of 0 means that the slope is North-facing, 90 East-facing, 180 South-facing, and
270 West-facing.

Since this study is taking place in the Southern Hemisphere, properties should
ideally be built on a north-facing slope so that they can remain in the
sunlight.

Use the :guilabel:`Aspect` algorithm of the
:menuselection:`Processing --> Raster terrain analysis` to get the ``aspect``
layer saved along with the ``slope``.

.. admonition:: Answer
   :class: dropdown

   Set your :guilabel:`Aspect` dialog up like this:

   .. figure:: img/answer_dem_aspect.png
      :align: center

   Your result:

     .. figure:: img/answer_aspect_result.png
        :align: center


|moderate| |FA| Reclassifying the Raster
----------------------------------------------------------------------

We know now that it has numerical values within a range from 0 through
360.
What we want to do is to *reclassify* this layer to other discrete
values (from 1 to 4), depending on the aspect:

* 1 = North (from 0 to 45 and from 315 to 360);
* 2 = East (from 45 to 135)
* 3 = South (from 135 to 225)
* 4 = West (from 225 to 315)

This operation can be achieved with the raster calculator, but the
formula would become very very large.

The alternative tool is the :guilabel:`Reclassify by table` tool
in :menuselection:`Raster analysis` in the
:guilabel:`Processing Toolbox`.

#. Open the tool
#. Choose :guilabel:`aspect` as the ``Input raster layer``
#. Click on the :guilabel:`...` of :guilabel:`Reclassification table`.
   A table-like dialog will pop up, where you can choose the minimum,
   maximum and new values for each class.
#. Click on the :guilabel:`Add row` button and add 5 rows.
   Fill in each row as the following picture and click :guilabel:`OK`:

   .. figure:: img/reclassify_table.png
      :align: center

   The method used by the algorithm to treat the threshold values of
   each class is defined by the :guilabel:`Range boundaries`.
#. Save the layer as :file:`reclassified.tif` in the
   :file:`exercise_data/raster_analysis/` folder

   .. figure:: img/reclassify_setup.png
      :align: center

#. Click on :guilabel:`Run`

If you compare the native :guilabel:`aspect` layer with the
:guilabel:`reclassified` one, there are not big differences.
But by looking at the legend, you can see that the values go from
``1`` to ``4``.

Let us give this layer a better style.

#. Open the :guilabel:`Layer Styling` panel
#. Choose :guilabel:`Paletted/Unique values`, instead of
   :guilabel:`Singleband gray`
#. Click on the :guilabel:`Classify` button to automatically fetch the
   values and assign them random colors:

   .. figure:: img/unique_style.png
      :align: center

The output should look like this (you can have different colors given
that they have been randomly generated):

.. figure:: img/reclassify_result.png
   :align: center

With this reclassification and the paletted style applied to the
layer, you can immediately differentiate the aspect areas.


|basic| |FA| Querying the raster
----------------------------------------------------------------------

Unlike vector layers, raster layers don't have an attribute table.
Each pixel contains one or more numerical values (singleband or
multiband rasters).

All the raster layers we used in this exercise consist of just one
band.
Depending on the layer, pixel values may represent elevation, aspect
or slope values.

How can we query the raster layer to get the value of a pixel?
We can use the |identify| :sup:`Identify Features` button!

#. Select the tool from the Attributes toolbar.
#. Click on a random location of the :guilabel:`srtm_41_19` layer.
   :guilabel:`Identify Results` will appear with the value of the
   band at the clicked location:

   .. figure:: img/identify_raster.png
      :align: center

#. You can change the output of the :guilabel:`Identify Results` panel
   from the current ``tree`` mode to a ``table`` one by selecting
   :guilabel:`Table` in the :guilabel:`View` menu at the bottom of the
   panel:

   .. figure:: img/identify_raster_table.png
      :align: center

Clicking each pixel to get the value of the raster could become
annoying after a while.
We can use the *Value Tool* plugin to solve this problem.

#. Go to :menuselection:`Plugins --> Manage/Install Plugins...`
#. In the :guilabel:`All` tab, type ``value t`` in the search box
#. Select the *Value Tool* plugin, press :guilabel:`Install Plugin`
   and then :guilabel:`Close` the dialog.

   .. figure:: img/value_tool.png
      :align: center

   The new :guilabel:`Value Tool` panel will appear.

   .. tip:: If you close the panel you can reopen it by enabling it in
      the :menuselection:`View --> Panels --> Value Tool` or by
      clicking on the icon in the toolbar.

#. To use the plugin just check the :guilabel:`Enable` checkbox and be
   sure that the ``srtm_41_19`` layer is active (checked) in the
   :guilabel:`Layers` panel.
#. Move the cursor over the map to see the value of the pixels.

   .. figure:: img/value_tool_query.png
      :align: center

#. But there is more.
   The Value Tool plugin allows you to query **all** the active raster
   layers in the :guilabel:`Layers` panel.
   Set the :guilabel:`aspect` and :guilabel:`slope` layers active
   again and hover the mouse on the map:

   .. figure:: img/value_tool_query_multi.png
      :align: center


|IC|
----------------------------------------------------------------------

You've seen how to derive all kinds of analysis products from a DEM.
These include hillshade, slope and aspect calculations.
You've also seen how to use the raster calculator to further analyze
and combine these results.
Finally you learned how to reclassify a layer and how to query the
results.

|WN|
----------------------------------------------------------------------

Now you have two analyses: the vector analysis which shows you the
potentially suitable plots, and the raster analysis that shows you the
potentially suitable terrain.
How can these be combined to arrive at a final result for this
problem?
That's the topic for the next lesson, starting in the next module.


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
.. |identify| image:: /static/common/mActionIdentify.png
   :width: 1.5em
.. |moderate| image:: /static/common/moderate.png
