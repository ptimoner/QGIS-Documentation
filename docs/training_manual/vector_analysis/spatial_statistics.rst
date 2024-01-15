|LS| Spatial Statistics
======================================================================

.. note:: Lesson developed by Linfiniti and S Motala (Cape Peninsula
   University of Technology)

Spatial statistics allows you to analyze and understand what is going
on in a given vector dataset.
QGIS includes many useful tools for statistical analysis.

**The goal for this lesson:** To know how to use QGIS' spatial
statistics tools within the :guilabel:`Processing Toolbox`.

|basic| |FA| Create a Test Dataset
----------------------------------------------------------------------

We will create a random set of points, to get a dataset to work with.

To do so, you will need a polygon dataset to define the area you
want to create the points in.

We will use the area covered by streets.

#. Start a new project
#. Add your ``roads`` dataset, as well as ``srtm_41_19`` (elevation
   data) found in :file:`exercise_data/raster/SRTM/`.

   .. note:: You might find that the SRTM DEM layer has a different
      CRS to that of the roads layer.
      QGIS is reprojecting both layers in a single CRS.
      For the following exercises this difference does not matter,
      but feel free to reproject (as shown earlier in this module).

#. Open :guilabel:`Processing` toolbox
#. Use the
   :menuselection:`Vector Geometry --> Minimum bounding geometry`
   tool to generate an area enclosing all the roads by selecting
   ``Convex Hull`` as the :guilabel:`Geometry Type`:

   .. figure:: img/roads_hull_setup.png
      :align: center

   As you know, if you don't specify the output, *Processing* creates
   temporary layers.
   It is up to you to save the layers immediately or at a later stage.

Creating random points
......................................................................

* Create 100 random points in this area using the tool at
  :menuselection:`Vector Creation --> Random points in layer bounds`,
  with a minimum distance of ``0.0``:

  .. figure:: img/random_points_setup.png
     :align: center

  .. note:: The yellow warning sign tells you that that parameter
     concerns distances.
     The :guilabel:`Bounding geometry` layer is in a Geographical
     Coordinate System and the algorithm is just reminding you this.
     For this example we won't use this parameter so you can ignore
     it.

If needed, move the generated random point to the top of the legend
to see them better:

.. figure:: img/random_points_result.png
   :align: center

Sampling the data
......................................................................

To create a sample dataset from the raster, you'll need to use the
:menuselection:`Raster Analysis --> Sample raster values` algorithm. This tool samples the raster at the locations of the points and
adds the raster values in new field(s) depending on the number of bands in the raster.

#. Open the :guilabel:`Sample raster values` algorithm dialog
#. Select ``Random_points`` as the layer containing sampling
   points, and the SRTM raster as the band to get values from.
   The default name of the new field is ``SAMPLE_`` (can varies
   depending on the QGIS version).
   You can change the name of the prefix if you want.

   .. figure:: img/sample_raster_dialog.png
      :align: center

#. Press :guilabel:`Run`

Now you can check the sampled data from the raster file in the
attribute table of the ``Sampled Points`` layer (or in a newly created
layer depending on the QGIS version).
In any case there will be in a new field with the name you have chosen.

A possible sample layer is shown here:

.. figure:: img/random_samples_result.png
   :align: center

The sample points are classified using the new field such
that red points are at a higher altitude.

You will be using this sample layer for the rest of the statistical
exercises.

|basic| |FA| Basic Statistics
----------------------------------------------------------------------

Now get the basic statistics for this layer.

#. Click on the |sum| :sup:`Show statistical summary` icon in the
   :guilabel:`Attributes Toolbar`.
   A new panel will pop up.
#. In the dialog that appears, specify the ``Sampled Points`` layer as
   the source.
#. Select the new field in the field combo box.
   This is the field you will calculate statistics for.
#. The :guilabel:`Statistics` Panel will be automatically updated
   with the calculated statistics:

   .. figure:: img/basic_statistics_results.png
      :align: center

   .. note:: You can copy the values by clicking on the |editCopy|
      :sup:`Copy Statistics To Clipboard` button and paste the results
      into a spreadsheet.

#. Close the :guilabel:`Statistics` Panel when done

Many different statistics are available:

Count
  The number of samples/values.

Sum
  The values added together.

Mean
  The mean (average) value is simply the sum of the values divided by
  the number of values.

Median
  If you arrange all the values from smallest to greatest, the middle
  value (or the average of the two middle values, if N is an even
  number) is the median of the values.

St Dev (pop)
  The standard deviation.
  Gives an indication of how closely the values are clustered around
  the mean.
  The smaller the standard deviation, the closer values tend to be to
  the mean.

Minimum
  The minimum value.

Maximum
  The maximum value.

Range
  The difference between the minimum and maximum values.

Q1
  First quartile of the data.

Q3
  Third quartile of the data.

Missing (null) values
  The number of missing values.


|IC|
----------------------------------------------------------------------

QGIS has a number of tools for analyzing the spatial statistical
properties of datasets.


|WN|
----------------------------------------------------------------------

Now that we have covered vector analysis, why not see what can be
done with rasters?
That is what we will do in the next module!


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
.. |editCopy| image:: /static/common/mActionEditCopy.png
   :width: 1.5em
.. |fileSave| image:: /static/common/mActionFileSave.png
   :width: 1.5em
.. |moderate| image:: /static/common/moderate.png
.. |radioButtonOn| image:: /static/common/radiobuttonon.png
   :width: 1.5em
.. |sum| image:: /static/common/mActionSum.png
   :width: 1.2em
