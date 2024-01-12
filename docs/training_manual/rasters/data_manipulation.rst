|LS| Working with Raster Data
======================================================================

Os dados raster são bastante diferentes dos dados vetoriais.
Dados vetoriais têm características discretas com geometrias
construídas a partir de vértices, e talvez conectadas com linhas
e/ou áreas. Dados raster, no entanto, são como qualquer imagem.
Embora possam retratar várias propriedades de objetos no mundo real,
esses objetos não existem como objetos separados. Em vez disso,
eles são representados usando pixels com valores diferentes.

During this module you are going to use raster data to supplement your
existing GIS analysis.

**The goal for this lesson:** To learn how to work with raster data in
QGIS.

|basic| |FA| Loading Raster Data
----------------------------------------------------------------------

Raster data can be loaded with the same methods we used for vector
data.
However we suggest to use the :guilabel:`Browser` Panel.

#. Abra o painel :guilabel:`Browser` e expanda a pasta
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

Merging rasters
......................................................................

If you need to create a new raster layer and save it to disk you can
use the merge algorithm.

.. note:: Depending on how many raster files you are merging and their
   resolution, the new raster file created can be really big.
   Consider instead to create a raster catalog as described in the
   :ref:`Create a Virtual Raster <tm_virtual_raster>` section.

#. Clique no algoritmo :guilabel:`Merge` no menu
   :menuselection:`GDAL --> Raster miscellaneous`.
#. Use the
   :guilabel:`...` button to choose
   which layers you want to merge.

#. Se você conhece a biblioteca GDAL, também pode adicionar suas próprias opções
   abrindo o menu :guilabel:`Advanced parameters`.

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

.. |FA| replace:: Siga o Passo a Passo:
.. |IC| replace:: Em Conclusão
.. |LS| replace:: Lição:
.. |TY| replace:: Tente Você Mesmo
.. |WN| replace:: O Que Vem a Seguir?
.. |basic| image:: /static/common/basic.png
.. |hard| image:: /static/common/hard.png
