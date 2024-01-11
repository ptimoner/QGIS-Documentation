|LS| Reprojecting and Transforming Data
======================================================================

Falemos novamente sobre Sistemas de Referência de Coordenadas (CRSs). Já mencionamos isso
brevemente antes, mas não discutimos o que isso
significa na prática.

**The goal for this lesson:** To reproject and transform vector datasets.

|basic| |FA| Projections
----------------------------------------------------------------------

O Sistema de Referência de Coordenadas (CRS) no qual todos os dados,
assim como o próprio mapa, estão agora é chamado WGS84.
Este é um Sistema de Coordenadas Geográficas (GCS) muito
comum para representação de dados. No entanto, há um problema,
como veremos.

#. Save your current map
#. Em seguida, abra o mapa do mundo, que você encontrará no arquivo
   :file:`exercise_data/world/world.qgs`
#. Zoom in to South Africa by using the :guilabel:`Zoom In` tool
#. ente definir uma escala no campo :guilabel:`Scale` que está na Barra de Status ao
   *Statusbar* longo da parte inferior da tela.
   Enquanto estiver sobre a África do Sul, defina esse valor para ``1:5 000 000``
   (um para cinco milhões).
#. Pan around the map while keeping an eye on the :guilabel:`Scale`
   field

Perceba a mudança na escala? Isso ocorre porque você está se afastando do ponto
para o qual você ampliou em ``1:5 000 000``, que estava no centro da sua
tela. Ao redor desse ponto, a
escala é diferente.

To understand why, think about a globe of the Earth.
It has lines running along it from North to South.
These longitude lines are far apart at the equator, but they meet at
the poles.

Em um GCS, você está trabalhando nesta esfera, mas a sua tela é plana.
Quando você tenta representar a esfera em uma superfície plana,
ocorre distorção,
semelhante ao que aconteceria se cortasse uma bola de tênis e tentasse aplainá-la.
O que isso significa em um mapa é que as linhas de longitude permanecem igualmente
distantes uma das outras, mesmo nos polos (onde deveriam se encontrar).
Isso significa que, à medida que você se afasta do equador no seu mapa,
a escala dos objetos que você vê fica
cada vez maior. O que isso significa para
nós, na prática, é que não há escala
constante no nosso mapa!"

To solve this, let's use a Projected Coordinate System (PCS) instead.
A PCS "projects" or converts the data in a way that makes allowance
for the scale change and corrects it.
Therefore, to keep the scale constant, we should reproject our data to
use a PCS.

|basic| |FA| "On the Fly" Reprojection
----------------------------------------------------------------------

By default, QGIS reprojects data "on the fly". What this means is that even if
the data itself is in another CRS, QGIS can project it as if it were in a CRS of
your choice.

You can change the CRS of the project by clicking on the
|projectionEnabled| :sup:`Current projection` button in the bottom
right corner of QGIS.

#. In the dialog that appears, type the word ``global`` into the
   :guilabel:`Filter` field.
   A few CRSs should appear in the
   :guilabel:`Predefined Reference Systems` field below.
#. Select :guilabel:`WGS 84 / NSIDC EASE-Grid 2.0 Global | EPSG:6933`
   entry by clicking on it, and then click :guilabel:`OK`.

   Notice how the shape of South Africa changes.
   All projections work by changing the apparent shapes of objects on
   Earth.
#. Zoom to a scale of ``1:5 000 000`` again, as before.
#. Pan around the map.

   Notice how the scale stays the same!

"On the fly" reprojection is also used for combining datasets that are
in different CRSs.

#. Add another vector layer to your map which has the data for South
   Africa only.
   You will find it as :file:`exercise_data/world/RSA.shp`.
#. Load it. 
   A quick way to see its CRS is by hovering the mouse over the layer
   in the legend. It is ``EPSG:3410``.

   What do you notice?

   The layer is visible even if it has a different CRS from the
   :guilabel:`continents` one.


|moderate| |FA| Saving a Dataset to Another CRS
----------------------------------------------------------------------

Sometimes you need to export an existing dataset with another CRS.
As we will see in the next lesson, if you need to make distance
calculations on layer, it is always better to have the layer in a
projected coordinate system.

Be aware that the 'on the fly' reprojection is related to the
**project** and not to single layers.
This means that a layer can have a different CRS from the project even
if you see it in the *correct* position.

You can easily export the layer with another CRS.

#. Add the ``buildings`` dataset from :file:`training_data.gpkg`
#. Right-click on the ``buildings`` layer in the :guilabel:`Layers`
   panel
#. Select :menuselection:`Export --> Save Features As...` in the menu
   that appears.
   You will be shown the :guilabel:`Save Vector Layer as...` dialog.
#. Click on the :guilabel:`Browse` button next to the
   :guilabel:`File name` field
#. Navigate to :file:`exercise_data/` and specify the name of the new
   layer as :file:`buildings_reprojected.shp`.
#. Change the value of the :guilabel:`CRS`.
   Only the recent CRSs used will be shown in the drop-down menu.
   Click on the |setProjection| :sup:`Select projection` button next
   to the drop-down menu.
#. The :guilabel:`Coordinate Reference System Selector` dialog will
   appear.
   In its :guilabel:`Filter` field, search for ``34S``.
#. Select :guilabel:`WGS 84 / UTM zone 34S | EPSG:32734` from the list

   .. figure:: img/CRSselector.png
      :align: center

#. Leave the other options unchanged.
   The :guilabel:`Save Vector Layer as...` dialog now looks like this:

   .. figure:: img/save_vector_dialog.png
      :align: center

#. Click :guilabel:`OK`

You can now compare the old and new projections of the layer and see that they
are in two different CRS but they are still overlapping.


|IC|
----------------------------------------------------------------------

Different projections are useful for different purposes. By choosing the
correct projection, you can ensure that the features on your map are being
represented accurately.

|FR|
----------------------------------------------------------------------

Materials for the *Advanced* section of this lesson were taken from `this
article <https://anitagraser.com/2012/03/18/beautiful-global-projections-adding-custom-projections-to-qgis/>`_.

Read further information on :ref:`Coordinate Reference Systems <gis_coord_ref_system>`.

|WN|
----------------------------------------------------------------------

In the next lesson you will learn how to analyze vector data using
QGIS' various vector analysis tools.


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
.. |basic| image:: /static/common/basic.png
.. |hard| image:: /static/common/hard.png
.. |moderate| image:: /static/common/moderate.png
.. |projectionEnabled| image:: /static/common/mIconProjectionEnabled.png
   :width: 1.5em
.. |setProjection| image:: /static/common/mActionSetProjection.png
   :width: 1.5em
.. |symbologyAdd| image:: /static/common/symbologyAdd.png
   :width: 1.5em
