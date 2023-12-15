|LS| Working with Raster Data
======================================================================

Raster data is quite different from vector data.
Vector data has discrete features with geometries constructed out of
vertices, and perhaps connected with lines and/or areas.
Raster data, however, is like any image.
Although it may portray various properties of objects in the real
world, these objects don't exist as separate objects.
Rather, they are represented using pixels with different values.

During this module you are going to use raster data to supplement your
existing GIS analysis.

**The goal for this lesson:** To learn how to work with raster data in
QGIS.

|basic| |FA| Loading Raster Data
----------------------------------------------------------------------

Raster data can be loaded with the same methods we used for vector
data.
However we suggest to use the :guilabel:`Browser` Panel.

#. Open the :guilabel:`Browser` Panel and expand the
   :file:`exercise_data/raster` folder.
#. Load all the data in this folder:

   * :file:`3320C_2010_314_RGB_LATLNG.tif`
   * :file:`3320D_2010_315_RGB_LATLNG.tif`
   * :file:`3420B_2010_328_RGB_LATLNG.tif`
   * :file:`3420C_2010_327_RGB_LATLNG.tif`

You should see the following map:

.. figure:: img/raster_step_one.png
   :align: center

There we have it - four aerial images covering our study area.

|hard| Transforming Raster Data
----------------------------------------------------------------------

Reprojecting rasters
......................................................................

Open :guilabel:`Warp (reproject)` from 
:menuselection:`GDAL --> Raster projections`.

You can also reproject virtual rasters (catalogs), enable
multithreaded processing, and more.

.. figure:: img/warp_rasters.png
   :align: center

Merging rasters
......................................................................

If you need to create a new raster layer and save it to disk you can
use the merge algorithm.

.. note:: Depending on how many raster files you are merging and their
   resolution, the new raster file created can be really big.
   Consider instead to create a raster catalog as described in the
   :ref:`Create a Virtual Raster <tm_virtual_raster>` section.

#. Click on the :guilabel:`Merge` algorithm from the
   :menuselection:`GDAL --> Raster miscellaneous` menu.
#. As we did for the
   :ref:`Create a Virtual raster <tm_virtual_raster>`, use the
   :guilabel:`...` button to choose which layers you want to merge.

   You can also specify a Virtual raster as input, and then all of the
   rasters that it consists of will be processed.
#. If you know the GDAL library, you can also add your own options by
   opening the :guilabel:`Advanced parameters` menu.

.. figure:: img/merge_rasters.png
   :align: center

|IC|
----------------------------------------------------------------------

QGIS makes it easy to include raster data into your existing projects.

|WN|
----------------------------------------------------------------------

Next, we'll use raster data that isn't aerial imagery, and see how
symbolization is useful in the case of rasters as well.


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
.. |hard| image:: /static/common/hard.png
