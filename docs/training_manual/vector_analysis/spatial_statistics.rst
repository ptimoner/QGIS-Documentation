|LS| Spatial Statistics
======================================================================

.. note:: Lesson developed by Linfiniti and S Motala (Cape Peninsula
   University of Technology)

Spatial statistics allows you to analyze and understand what is going
on in a given vector dataset.
QGIS includes many useful tools for statistical analysis.

**O objetivo desta lição:** aprender como usar as ferramentas de
estatísticas espaciais do QGIS dentro do :guilabel:`Processing Toolbox`.

|basic| |FA| Create a Test Dataset
----------------------------------------------------------------------

We will create a random set of points, to get a dataset to work with.

To do so, you will need a polygon dataset to define the area you
want to create the points in.

We will use the area covered by streets.

#. Start a new project
#. Adicione o conjunto de dados ``roads``, assim como o ``srtm_41_19`` (dado de
   altitude) encontrado em :file:`exercise_data/raster/SRTM/`.

   .. note:: Você pode perceber que a camada SRTM DEM tem um SRC
      diferente da camada de estradas. O QGIS está reprojetando
      ambas as camadas em um único SRC. Para os exercícios seguintes,
      essa diferença não importa, mas sinta-se à vontade para reprojetar
      (como mostrado anteriormente neste módulo).

#. Abra o :guilabel:`Processing` toolbox
#. Use a ferramenta
   :menuselection:`Vector Geometry --> Minimum bounding geometry`
   para gerar uma área que envolve todas as estradas, selecionando
   ``Convex Hull`` para :guilabel:`Geometry Type`:

   .. figure:: img/roads_hull_setup.png
      :align: center

   Como você sabe, se você não especificar a saída, o *Processamento*
   cria camadas temporárias. Fica a seu critério salvar as camadas
   imediatamente ou em um momento posterior.

Creating random points
......................................................................

* Crie 100 pontos aleatórios nesta área usando a ferramenta
  :menuselection:`Vector Creation --> Random points in layer bounds`,
  com uma distância mínima de ``0.0``:

  .. figure:: img/random_points_setup.png
     :align: center

  .. note:: O sinal de aviso amarelo informa que esse parâmetro
     se refere a distâncias.
     A camada :guilabel:`Bounding geometry` layer está em um Sistema
     de Coordenadas Geográficas e o algoritmo está apenas lembrando
     você disso. Para este exemplo, não usaremos esse parâmetro,
     então você pode ignorá-lo.

Se necessário, mova os pontos aleatórios gerados para o
topo da legenda para vê-los melhor:

.. figure:: img/random_points_result.png
   :align: center

Sampling the data
......................................................................

Para criar um conjunto de dados de amostra a partir do raster, você precisará usar o algoritmo
:menuselection:`Raster Analysis --> Sample raster values`. Essa ferramenta amostra o raster nos locais dos pontos e adiciona os valores do raster em novos campos, dependendo do número de bandas no raster.

#. Open the :guilabel:`Sample raster values` algorithm dialog
#. Selecione ``Random_points`` como a camada contendo pontos de amostragem,
   e o raster SRTM como a banda para obter valores.
   O nome padrão do novo campo é ``SAMPLE_`` (pode variar conforme a 
   versão do QGIS).
   Você pode alterar o nome do prefixo se desejar.

   .. figure:: img/sample_raster_dialog.png
      :align: center

#. Press :guilabel:`Run`

Now you can check the sampled data from the raster file in the
attribute table of the ``Sampled Points`` layer.
They will be in a new field with the name you have chosen.

A possible sample layer is shown here:

.. figure:: img/random_samples_result.png
   :align: center

Os pontos de amostra são classificados usando o novo campo,
de modo que os pontos vermelhos estão a uma altitude mais elevada.

You will be using this sample layer for the rest of the statistical
exercises.

|basic| |FA| Basic Statistics
----------------------------------------------------------------------

Now get the basic statistics for this layer.

#. Clique no ícone |sum| :sup:`Show statistical summary` no
   :guilabel:`Attributes Toolbar`.
   Um novo painel aparecerá.
#. In the dialog that appears, specify the ``Sampled Points`` layer as
   the source.
#. Selecione o novo campo na caixa de seleção de campos.
   Este é o campo para o qual você calculará estatísticas.
#. The :guilabel:`Statistics` Panel will be automatically updated
   with the calculated statistics:

   .. figure:: img/basic_statistics_results.png
      :align: center

   .. note:: Você pode copiar os valores clicando no botão |editCopy|
      :sup:`Copy Statistics To Clipboard` e colar os resultados
      em uma planilha.

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

O QGIS possui várias ferramentas para analisar as propriedades
estatísticas espaciais de conjuntos de dados.


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

.. |FA| replace:: Siga o Passo a Passo:
.. |IC| replace:: Em Conclusão
.. |LS| replace:: Lição:
.. |TY| replace:: Tente Você Mesmo
.. |WN| replace:: O Que Vem a Seguir?
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
