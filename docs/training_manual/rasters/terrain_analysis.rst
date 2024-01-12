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

Vamos utilizar a mesma camada MDE que utilizámos na lição anterior.
Se está a começar este capítulo do zero, use o painel
:guilabel:`Browser` e carregue o arquivo
:file:`raster/SRTM/srtm_41_19.tif`.

A camada MDE mostra-lhe a elevação do terreno, mas pode
as vezes, parecer um pouco abstrata.
Contém toda a informação 3D sobre o terreno de que necessita,
mas não se parece com um objeto 3D.
Para obter uma melhor impressão do terreno, é possível calcular
um *hillshade* (relevo sombreado), que é uma imagem raster que mapeia o terreno
usando luz e sombra para criar uma imagem de aspeto 3D.

Vamos utilizar algoritmos do menu
:menuselection:`Raster --> Raster terrain analysis`.

#. Clique no menu :menuselection:`Hillshade`
#. O algoritmo permite-lhe especificar a posição da luz:
   :guilabel:`Azimuth` tem valores de 0 (Norte) a 90
   (Este), 180 (Sul) e 270 (Oeste), enquanto que o
   :guilabel:`Vertical angle` define a altura da fonte de luz
   (0 a 90 graus).
#. We will use the following values:

   * :guilabel:`Z factor` at ``1.0``
   * :guilabel:`Azimuth (horizontal angle)` para ``300.0``\°
   * :guilabel:`Vertical angle` para ``40.0``\°

   .. figure:: img/hillshade_explanation.png
      :align: center

#. Salve o resultado numa nova pasta :file:`exercise_data/raster_analysis/`
   com o nome de ``hillshade``
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

#. Altere a simbologia da camada orginal :guilabel:`srtm_41_19` para utilizar
   o esquema :guilabel:`Pseudocolor` como no exercício anterior
#. Esconda todas as camadas exceto as camadas :guilabel:`srtm_41_19` e
   :guilabel:`hillshade`
#. Clique e arraste a camada :guilabel:`srtm_41_19` para ficar por baixo da camada :guilabel:`hillshade`
   no painel :guilabel:`Layers`
#. Defina a camada :guilabel:`hillshade` para ser transparente clicando na guia
   :guilabel:`Transparency` nas propriedades da camada
#. Defina a :guilabel:`Global opacity` para ``50%``.

   You'll get a result like this:

   .. figure:: img/hillshade_pseudocolor.png
      :align: center

#. Desligue e volte a ligar a camada :guilabel:`hillshade` no painel
   :guilabel:`Layers` para ver a diferença que faz.

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

We have used the *Raster calculator* to do calculations on raster
layers.
There is another powerful tool that we can use to extract information
from existing layers.

Back to the ``aspect`` layer.
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

.. |FA| replace:: Siga o Passo a Passo:
.. |IC| replace:: Em Conclusão
.. |LS| replace:: Lição:
.. |TY| replace:: Tente Você Mesmo
.. |WN| replace:: O Que Vem a Seguir?
.. |basic| image:: /static/common/basic.png
.. |identify| image:: /static/common/mActionIdentify.png
   :width: 1.5em
.. |moderate| image:: /static/common/moderate.png
