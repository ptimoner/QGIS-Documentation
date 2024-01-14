|LS| Vector Analysis
======================================================================

Os dados vetoriais também podem ser analisados para revelar como diferentes
características interagem entre si no espaço. Existem muitas funções
relacionadas à análise, então não passaremos por todas elas.
Em vez disso, formularemos uma pergunta e tentaremos resolvê-la
usando as ferramentas fornecidas pelo QGIS.

**The goal for this lesson:** To ask a question and solve it using
analysis tools.


|basic| The GIS Process
----------------------------------------------------------------------

Before we start, it would be useful to give a brief overview of a
process that can be used to solve a problem.
The way to go about it is:

#. State the Problem
#. Get the Data
#. Analyze the Problem
#. Present the Results


|basic| The Problem
----------------------------------------------------------------------

Let's start off the process by deciding on a problem to solve.
For example, you are an estate agent and you are looking for a
residential property in |majorUrbanName| for clients who have the
following criteria:

#. Precisar esta em |majorUrbanName|
#. It must be within reasonable driving distance of a school (say 1km)
#. It must be more than 100m squared in size
#. Closer than 50m to a main road
#. Closer than 500m to a restaurant


|basic| The Data
----------------------------------------------------------------------

To answer these questions, we are going to need the following data:

#. The residential properties (buildings) in the area
#. The roads in and around the town
#. The location of schools and restaurants
#. The size of buildings















|basic| |FA| Start a Project and get the Data
----------------------------------------------------------------------

We first need to load the data to work with.

#. Start a new QGIS project
#. Se você quiser, pode adicionar um mapa de fundo. Abra
   :guilabel:`Browser` e carregue o mapa de fundo :guilabel:`OSM`
   do menu :guilabel:`XYZ Tiles`.

   .. figure:: img/osm_swellendam.png
      :align: center

#. Na base de dados GeoPackage :file:`training_data.gpkg`, você
   encontrará a maioria dos conjuntos de dados que usaremos neste capítulo:

   #. ``buildings``
   #. ``roads``
   #. ``restaurants``
   #. ``schools``

   Carregue-os, e também :file:`landuse.sqlite`.

#. Faça zoom para a extensão da camada para ver |majorUrbanName|, África do Sul.

   Antes de prosseguir, filtraremos a camada :guilabel:`roads`,
   a fim de ter apenas alguns tipos específicos de estradas para trabalhar.

   Algumas estradas são listadas como ``unclassified``,
   ``tracks``, ``path`` and ``footway``.
   Queremos excluir essas do nosso conjunto de dados e focar nos outros tipos de estradas,
   mais adequados para este exercício.

   Além disso, os dados podem não estar atualizados em todos os lugares,
   e também excluiremos valores ``NULL``.

#. Clique com o botão direito na camada ``roads`` e escolhe :guilabel:`Filter...`.
#. In the dialog that pops up we filter these features with the following expression::

     "highway" NOT IN ('footway', 'path', 'unclassified', 'track') AND "highway" IS NOT NULL

   A concatenação dos dois operadores ``NOT`` e ``IN`` exclui todas as feições que têm esses
   valores no campo ``highway``.

   ``IS NOT NULL`` combinado com o operador ``AND`` exclui estradas sem valor no campo
   ``highway``.

   Observe o ícone |indicatorFilter| ao lado da camada :guilabel:`roads`.
   Isso ajuda a lembrar que um filtro está ativado nesta camada, então
   algumas feições podem não estar disponíveis no projeto.

The map with all the data should look like the following one:

.. figure:: img/osm_swellendam_2.png
   :align: center


|basic| |TY| Convert Layers' CRS
----------------------------------------------------------------------

Because we are going to be measuring distances within our layers, we need to
change the layers' CRS. To do this, we need to select each layer in turn,
save the layer to a new one with our new projection, then import that new
layer into our map.

Você tem muitas opções diferentes, por exemplo, pode exportar cada camada
como um conjunto de dados no formato ESRI Shapefile, pode anexar as camadas
a um arquivo GeoPackage existente, ou pode criar outro arquivo GeoPackage e
preenchê-lo com as novas camadas reprojetadas.
Vamos mostrar a última opção, para que o :file:`training_data.gpkg` permaneça
limpo.
Sinta-se à vontade para escolher o melhor fluxo de trabalho para você.

.. note:: Neste exemplo, estamos utilizando o SRC *WGS 84 / UTM zone 34S*
   .
   

#. Clique com o botão direito na camada :guilabel:`roads` no painel
   :guilabel:`Layers`
#. Clique :guilabel:`Export --> Save Features As...`
#. Na janela :guilabel:`Save Vector Layer As` escolhe
   :guilabel:`GeoPackage` as :guilabel:`Format`
#. Clique em :guilabel:`...` para o :guilabel:`File name`, e nomeie
   o novo GeoPackage ``vector_analysis``
#. Altere o :guilabel:`Layer name` para ``roads_34S``
#. Altere o :guilabel:`CRS` para *WGS 84 / UTM zone 34S*
#. Clique em :guilabel:`OK`:

   .. figure:: img/save_roads_34S.png
      :align: center

   Isso criará o novo banco de dados GeoPackage e adicionará a camada ``roads_34S``.

#. Repita este processo para cada camada, criando uma nova camada no arquivo GeoPackage
   :file:`vector_analysis.gpkg` com ``_34S`` adicionado ao nome original.
   
   No macOS, pressione o botão :guilabel:`Replace` na caixa de diálogo que aparece
   para permitir que o QGIS substitua o GeoPackage existente.

   .. note:: Quando escolher salvar uma camada em um GeoPackage existente,
      o QGIS **adicionará** essa camada ao lado das camadas existentes no GeoPackage,
      se nenhuma camada com o mesmo nome já existir.

#. Remova cada uma das camadas antigas do projeto.
#. Depois de concluir o processo para todas as camadas, clique com o botão direito em
   qualquer camada e selecione :guilabel:`Zoom to layer extent` para focar o mapa na
   área de interesse.

Agora que convertemos os dados OSM para uma projeção UTM,
podemos começar nossos cálculos.

|basic| |FA| Analyzing the Problem: Distances From Schools and Roads
----------------------------------------------------------------------

QGIS allows you to calculate distances between any vector object.

#. Certifique-se de que apenas as camadas ``roads_34S`` and ``buildings_34S``
   estejam visíveis (para simplificar o mapa enquanto você trabalha)
#. Clique em :menuselection:`Processing --> Toolbox` para abrir
   o *núcleo* analítico do QGIS.
   Basicamente, **todos** os  algoritmos (para análise vetorial **e** raster)
   estão disponíveis nesta caixa de ferramentas.
#. Começamos calculando a área ao redor das estradas ``roads_34S`` utilizando
   o algoritmo de :guilabel:`Buffer`. Você pode encontrâ-lo no grupo
   :menuselection:`Vector Geometry`.

   .. figure:: img/processing_buffer_1.png
      :align: center

   Or you can type ``buffer`` in the search menu in the upper part of
   the toolbox:

   .. figure:: img/processing_buffer_2.png
      :align: center

#. Double click on it to open the algorithm dialog
#. Selecione ``roads_34S`` como :guilabel:`Input layer`, defina a
   :guilabel:`Distance` para 50 e use os valores padrão para
   o restante dos parâmetros.

   .. figure:: img/vector_buffer_setup.png
      :align: center

#. O padrão para o parâmetro :guilabel:`Distance`  é em metros porque nosso conjunto de
   dados de entrada está em um Sistema de Coordenadas Projetado que usa o
   metro como sua unidade básica de medida. Você pode usar a caixa de
   combinação para escolher outras unidades projetadas, como
   quilômetros, jardas, etc.

   .. note:: Se você estiver tentando fazer um buffer em uma camada com
      um Sistema de Coordenadas Geográficas, o Processamento emitirá um aviso
      e sugerirá reprojetar a camada para um Sistema de Coordenadas métrico.

#. Por padrão, *Processing* cria camadas temporárias e as adiciona ao painel de
   :guilabel:`Layers`.
   Você também pode anexar o resultado ao banco de dados GeoPackage por:
   
   #. Clicando no botão :guilabel:`...` e escolhendo
      :guilabel:`Save to GeoPackage...`
   #. Nomeando a nova camada ``roads_buffer_50m``
   #. Salvando-a no arquivo :file:`vector_analysis.gpkg` file

   .. figure:: img/buffer_saving.png
      :align: center

#. Clique em :guilabel:`Run`, e depois fecha a janela
   :guilabel:`Buffer`

   Now your map will look something like this:

   .. figure:: img/roads_buffer_result.png
      :align: center

Se a sua nova camada estiver no topo da lista dos :guilabel:`Layers`, provavelmente ela
obscurecerá grande parte do seu mapa, mas isso lhe dará todas as áreas na sua região
que estão a até 50 metros de uma estrada.

Observe que existem áreas distintas dentro do seu buffer,
que correspondem a cada estrada individual. Para resolver esse problema:

#. Desmarque a camada :guilabel:`roads_buffer_50m` e crie de novo
   o buffer com a opção :guilabel:`Dissolve results` ativada.

   .. figure:: img/dissolve_buffer_setup.png
      :align: center

#. Salve o resultado como :guilabel:`roads_buffer_50m_dissolved`
#. Clique em :guilabel:`Run` e feche a janela :guilabel:`Buffer`

Depois de adicionar a camada ao painel :guilabel:`Layers`, ela
parecerá assim:

.. figure:: img/dissolve_buffer_results.png
   :align: center

Now there are no unnecessary subdivisions.

.. note:: O *Short Help* no lado direito da janela explica
   como o algoritmo funciona.
   Se precisar de mais informações, basta clicar no botão
   :guilabel:`Help` na parte inferior para abrir um guia
   mais detalhado do algoritmo."

.. _backlink-vector-analysis-basic-1:

|basic| |TY| Distance from schools
----------------------------------------------------------------------

Use the same approach as above and create a buffer for your schools.

Deve ter um raio de ``1 km``.
Salve a nova camada no arquivo :file:`vector_analysis.gpkg` como ``schools_buffer_1km_dissolved``.

.. admonition:: Answer
   :class: dropdown

   * Sua caixa de diálogo de buffer deve se parecer com esta:

     .. figure:: img/schools_buffer_setup.png
        :align: center

   A :guilabel:`Buffer distance` é :guilabel:`1` kilômetro.

   * Os valor para :guilabel:`Segments to approximate` está definido para :guilabel:`20`. 
     Isto é opcional, mas é recomendado, pois torna os
     buffers de saída mais suaves. Compare isso:

     .. figure:: img/schools_buffer_5.png
        :align: center

     To this:

     .. figure:: img/schools_buffer_6.png
        :align: center

   A primeira imagen mostra o buffer com :guilabel:`Segments to approximate`
   definido para :guilabel:`5` e a segunda mostra o valor definido para :guilabel:`20`.
   No nosso exemplo, a diferença é sutil, mas você pode ver que as bordas do buffer
   são mais suaves com o valor mais alto.

|basic| |FA| Overlapping Areas
----------------------------------------------------------------------

Agora identificamos áreas onde a estrada está a menos de 50 metros e áreas onde há
uma escola dentro de 1 km (linha direta, não por estrada). Mas obviamente,
queremos apenas as áreas onde ambos esses critérios são satisfeitos. Para
fazer isso, precisaremos usar a ferramenta :guilabel:`Intersect` tool.
Você pode encontrá-la no grupo :menuselection:`Vector Overlay` na caixa :guilabel:`Processing Toolbox`.


#. Use as duas camadas de buffer como :guilabel:`Input layer` e
   :guilabel:`Overlay layer`, escolha o GeoPackage :file:`vector_analysis.gpkg`
   e :guilabel:`Intersection` com :guilabel:`Layer name`
   ``road_school_buffers_intersect``.
   Deixe o restante como sugerido (padrão).

   .. figure:: img/school_roads_intersect.png
      :align: center

#. Clique no botão :guilabel:`Run`.

   In the image below, the blue areas are where both of the distance
   criteria are satisfied.

   .. figure:: img/intersect_result.png
      :align: center

#. You may remove the two buffer layers and only keep the one that
   shows where they overlap, since that's what we really wanted to
   know in the first place:

   .. figure:: img/final_intersect_result.png
      :align: center

.. _select-by-location:

|basic| |FA| Extrair os Edifícios
----------------------------------------------------------------------

Now you've got the area that the buildings must overlap.
Next, you want to extract the buildings in that area.

#. Procure a entrada
   :menuselection:`Vector Selection --> Extract by location`
   no *Processing Toolbox*
#. Selecione ``buildings_34S`` em :guilabel:`Extract features from`.
   Marque :guilabel:`intersect` em
   :guilabel:`Where the features (geometric predicate)`,
   selecione a camada de interseção do buffer em
   :guilabel:`By comparing to the features from`.
   Salve o arquivo :file:`vector_analysis.gpkg`, e nomeie a camada
   ``well_located_houses``.

   .. figure:: img/location_select_dialog.png
      :align: center

#. Clique :guilabel:`Run` e feche a janela.
#. Você provavelmente perceberá que não houve muita mudança aparente. Se for o
   caso, mova a camada :guilabel:`well_located_houses` para o topo da lista de camadas e, em
   seguida, dê zoom.

   .. figure:: img/select_zoom_result.png
      :align: center

   The red buildings are those which match our criteria, while the
   buildings in green are those which do not.
#. Agora você tem duas camadas separadas e pode remover ``buildings_34S``
   da lista de camadas.


|moderate| |TY| Further Filter our Buildings
----------------------------------------------------------------------

We now have a layer which shows us all the buildings within 1km of a
school and within 50m of a road.
We now need to reduce that selection to only show buildings which are
within 500m of a restaurant.

Using the processes described above, create a new layer called
:guilabel:`houses_restaurants_500m` which further filters your
:guilabel:`well_located_houses` layer to show only those which are
within 500m of a restaurant.

.. admonition:: Answer
   :class: dropdown

   Para criar a nova camada :guilabel:`houses_restaurants_500m`, Vamos passar por um
   processo de duas etapas:
   
   #. First, create a buffer of 500m around the restaurants and add the layer to
      the map:

      .. figure:: img/restaurants_buffer.png
         :align: center

      .. figure:: img/restaurants_buffer_result.png
         :align: center

   #. Next, extract buildings within that buffer area:

      .. figure:: img/select_within_restaurants.png
         :align: center

   Your map should now show only those buildings which are within 50m of a road,
   1km of a school and 500m of a restaurant:

   .. figure:: img/restaurant_buffer_result.png
      :align: center

|basic| |FA| Select Buildings of the Right Size
----------------------------------------------------------------------

To see which buildings are of the correct size (more than 100 square
meters), we need to calculate their size.

#. Selecione a camada :guilabel:`houses_restaurants_500m` e abra o
   *Field Calculator* clicando no botão |calculateField|
   :sup:`Open Field Calculator` na barra de ferramentas principal
   ou na janela da tabela de atributos.
#. Selecione :guilabel:`Create a new field`, defina o
   :guilabel:`Output field name` para ``AREA``, escolhe
   :guilabel:`Decimal number (real)` como
   :guilabel:`Output field type`, e escolhe ``$area`` do grupo
   :menuselection:`Geometry`.

   .. figure:: img/buildings_area_calculator.png
      :align: center

   The new field ``AREA`` will contain the area of each building in
   square meters.
#. Clique :guilabel:`OK`.
   O campo ``AREA`` foi adicionado no final da tabela de
   atributos.
#. Clique no botão |toggleEditing| :sup:`Toggle Editing` para encerrar
   a edição, and salve as alterações quando solicitado.
#. Na aba :menuselection:`Source` das propiedades da camada, defina
   o :guilabel:`Provider Feature Filter` para ``"AREA >= 100``.

   .. figure:: img/buildings_area_query.png
      :align: center

#. Clique em :guilabel:`OK`.

Your map should now only show you those buildings which match our
starting criteria and which are more than 100 square meters in size.


|basic| |TY|
----------------------------------------------------------------------

Save your solution as a new layer, using the approach you learned
above for doing so.
The file should be saved within the same GeoPackage database, with
the name ``solution``.

|IC|
----------------------------------------------------------------------

Using the GIS problem solving approach together with QGIS vector
analysis tools, you were able to solve a problem with multiple
criteria quickly and easily.


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
.. |indicatorFilter| image:: /static/common/mIndicatorFilter.png
   :width: 1.5em
.. |majorUrbanName| replace:: Swellendam
.. |moderate| image:: /static/common/moderate.png
.. |toggleEditing| image:: /static/common/mActionToggleEditing.png
   :width: 1.5em
