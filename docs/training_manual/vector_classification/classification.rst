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

#. Abra a caixa de diálogo :guilabel:`Layer Properties` para a
   camada ``landuse``
#. Go to the :guilabel:`Symbology` tab
#. Click on the dropdown that says :guilabel:`Single Symbol` and
   change it to :guilabel:`Categorized`:

   .. figure:: img/categorised_styles.png
      :align: center

#. No novo painel, altere o valor (:guilabel:`Value`) para ``landuse`` e
   o a paleta de cores (:guilabel:`Color ramp`) para :guilabel:`Random colors`
#. Click the button labeled :guilabel:`Classify`

   .. figure:: img/categorised_style_settings.png
      :align: center

#. Click :guilabel:`OK`

   You'll see something like this:

   .. figure:: img/categorisation_result.png
      :align: center

#. Clique na seta (ou sinal de mais) ao lado de ``landuse`` no painel
   :guilabel:`Layers`, você verá as categorias explicadas:

   .. figure:: img/categories_explained.png
      :align: center

   Now our landuse polygons are colored and are classified so that
   areas with the same land use are the same color.

#. Se desejar, você pode alterar o símbolo de cada área de uso do solo
   clicando duas vezes no bloco de cor relevante no painel
   :guilabel:`Layers` ou na caixa de diálogo :guilabel:`Layer Properties`:

   .. figure:: img/change_layer_color.png
      :align: center

Notice that there is one category that's empty:

.. figure:: img/empty_category.png
   :align: center

Esta categoria vazia é usada para colorir quaisquer objetos que não tenham
um valor de uso do solo definido ou que tenham um valor *NULL*.
Pode ser útil manter essa categoria vazia para que as áreas com um valor *NULL* ainda
sejam representadas no mapa. Você pode querer mudar a cor para representar de forma mais 
evidente um valor em branco ou *NULL*.

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

.. |FA| replace:: Siga o Passo a Passo:
.. |IC| replace:: Em Conclusão
.. |LS| replace:: Lição:
.. |TY| replace:: Tente Você Mesmo
.. |WN| replace:: O Que Vem a Seguir?
.. |basic| image:: /static/common/basic.png
.. |calculateField| image:: /static/common/mActionCalculateField.png
   :width: 1.5em
.. |checkbox| image:: /static/common/checkbox.png
   :width: 1.3em
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
.. |equalCount| image:: /static/common/mClassificationEqualCount.png
   :width: 1.5em
