.. _tm_working_vector_data:

|LS| Atributos de Dados Vetoriais
===============================================================================

Os dados vetoriais são, sem dúvida, o tipo de dados mais comum no uso diário de SIG (Sistemas de Informação Geográfica). O modelo vetorial representa a localização e a forma de características geográficas usando pontos, linhas e polígonos (e para dados 3D também superfícies e volumes), enquanto suas outras propriedades são incluídas como atributos (muitas vezes apresentados como uma tabela no QGIS).

Up to now, none of the changes we have made to the map have been influenced by
the objects that are being shown. In other words, all the land use areas look
alike, and all the roads look alike. When looking at the map, the viewers don't
know anything about the roads they are seeing; only that there is a road of a
certain shape in a certain area.

But the whole strength of GIS is that all the objects that are visible on the
map also have attributes. Maps in a GIS aren't just pictures. They represent
not only objects in locations, but also information about those objects.


**The goal for this lesson:** To learn about the structure of vector data and
explore the attribute data of an object

|basic| |FA| Viewing Layer Attributes
-------------------------------------------------------------------------------

It's important to know that the data you will be working with does not only
represent **where** objects are in space, but also tells you **what** those
objects are.

Do exercício anterior, você deve ter a camada ``protected_areas``
carregada no seu mapa. Se ela não estiver carregada, você pode encontrar o conjunto de dados
:file:`protected_areas.shp` no diretório
:file:`exercise_data/shapefile`.

The polygons representing the protected areas constitute the **spatial data**,
but we can learn more about the protected areas by exploring the
**attribute table**.

#. No painel :guilabel:`Layers`, clique na camada ``protected_areas`` para selecioná-la.
#. No painel :menuselection:`Layer`, clique no botão |openTable|
   :sup:`Open Attribute Table` (também acessivel pelos botões das barras de ferramentas superiores).
   Isto abrirá uma nova janela mostrando a tabela  de atributos da camada ``protected_areas``.

   .. figure:: img/attribute_data_preview.png
     :align: center

   Uma linha é chamada de **record** e está associada a um **feature**
   na Tela de Mapa, como um polígono.
   Uma coluna é chamada de **field** (ou um **attribute**), e tem um nome que ajuda
   a descrevê-lo, como ``name`` ou ``id``.
   Valores nas células são conhecidos como **attribute values**.
   Essas definições são comumente usadas em SIG, então é bom se familiarizar com elas.

   Na camada ``protected_areas``, existem dois **features**, que são representadas pelos dois polígonos que vemos
   na Tela de Mapa.

   .. Note:: Para entender o que os campos e valores de atributo
      representam, pode ser necessário encontrar documentação (ou metadados) que descrevam
      o significado dos valores dos atributos.
      Essa informação geralmente está disponível com o criador do conjunto de dados.

Em seguida, vamos ver como um registro na tabela de atributos está vinculado a um polígono que vemos na Tela de Mapa.

#. Go back to the main QGIS window.
#. No menu :guilabel:`Edit --> Select`, clique no botão |selectRectangle| :guilabel:`Select Feature(s)`.
#. Certifique-se que a camada ``protected_areas`` continua estando selecionada no painel :guilabel:`Layers`.
#. Desloque o mouse até a Tela de Mapa e clique com o botão esquerdo no menor dos dois polígonos.
   O polígono ficará amarelo, indicando que está selecionado.

   .. figure:: img/select_polygon.png
      :align: center

#. Volte para a janela :guilabel:`Attribute Table`, e você deverá ver um
   registro (linha) destacado.
   Estes são os valores dos atributos do polígono selecionado.

   .. figure:: img/select_record.png
     :align: center

You can also select a feature using the Attribute Table.

#. Na janela :guilabel:`Attribute Table`, na extrema esquerda,
   clique no número da linha do registro que atualmente não está selecionado.

   .. figure:: img/select_record2.png
     :align: center

#. Volte para a janela principal do QGIS e olhe para a Tela de Mapa. Você deve
   ver o maior dos dois polígonos colorido de amarelo.
#. Para desselecionar a feição, vá até a janela :guilabel:`Attribute Table`
   e clique no botão |deselectActiveLayer| :sup:`Deselect all features from the layer`.

Às vezes há muitas feições mostradas na Tela de Mapa e pode ser difícil
ver qual feição está selecionada na Tabela de Atributos. Outra maneira de
identificar a localização de uma feição é utilizar a ferramenta :guilabel:`Flash Feature`
.

#. Na :guilabel:`Attribute Table`, clique com o botão direito em qualquer célula da
   linha que possui o valor de atributo ``r2855697`` no campo ``full_id``.
#. No menu de contexto, clique em :guilabel:`Flash Feature` e observe a
   Tela de Mapa.

   .. figure:: img/flash_feature.png
     :align: center

   You should see the polygon flash red a few times.  If you missed it,
   try it again.

Outra ferramenta útil é o :guilabel:`Zoom to Feature` tool, que indica ao QGIS para
dar zoom na feição de interesse.

#. Na :guilabel:`Attribute Table`, clique com o botão direito em qualquer célula da
   linha que possui o valor de atributo ``r2855697`` no campo ``full_id``.
#. No menu de contexto, clique em :guilabel:`Zoom to Feature`.

   .. figure:: img/zoom_to_feature.png
     :align: center

   Olhe para a Tela de Mapa. O polígono agora deve ocupar toda a extensão
da área da Tela de Mapa.

You may now close the attribute table.

.. _backlink-vector-explore-attribute-data:

|basic| |TY| Exploring Vector Data Attributes
-------------------------------------------------------------------------------

#. Quantos campos estão disponíveis na camada :guilabel:`rivers` ?
#. Tell us a bit about the ``town`` places in your dataset.
#. Abra a tabela de atributos para a camada :guilabel:`places`.
   Qual campo seria o mais útil para representar na forma de etiqueta (label),
   e por quê ?

.. admonition:: Answer
   :class: dropdown

   * Deve haver 9 campos na camada :guilabel:`rivers`:

     #. Selecione a camada no painel :guilabel:`Layers`.
     #. Clique com o botão direito e escolha :guilabel:`Open Attribute Table`,
        ou pressione o botão |openTable| no :guilabel:`Attributes Toolbar`
        (pode ser ativada no menu :menuselection:`View --> Toolbars`).
     #. Conte o número de colunas.

     Uma abordagem mais rápida pode ser dar um duplo clique na camada :guilabel:`rivers`,
     abrir a aba :menuselection:`Layer properties --> Fields`, onde você
     encontrará uma lista numerada dos campos da tabela.

   * Informações sobre as cidades estão disponíveis na camada :guilabel:`places`. Abra sua tabela de atributos como você fez com a       camada :guilabel:`rivers`:
     existem duas feições cujo atributo :guilabel:`place`
     está definido como ``cidade``: *Swellendam* and *Buffeljagsrivier*.
     Você pode adicionar comentários sobre outros campos desses dois registros, se desejar.

   * O campo ``name`` é o mais útil para mostrar como etiquetas (labels). Isso porque todos os seus valores são únicos para cada         objeto e é muito improvável que contenham valores *NULL*. Se seus dados contiverem alguns valores *NULL*, não se preocupe
     enquanto a maioria dos seus locais tiverem nomes.

|IC|
-------------------------------------------------------------------------------

You now know how to use the attribute table to see what is actually in the data
you're using. Any dataset will only be useful to you if it has the attributes
that you care about. If you know which attributes you need, you can quickly
decide if you're able to use a given dataset, or if you need to look for
another one that has the required attribute data.

|WN|
-------------------------------------------------------------------------------

Different attributes are useful for different purposes. Some of them can be
represented directly as text for the map user to see. You'll learn how to do
this in the next lesson.


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
.. |deselectActiveLayer| image:: /static/common/mActionDeselectActiveLayer.png
   :width: 1.5em
.. |openTable| image:: /static/common/mActionOpenTable.png
   :width: 1.5em
.. |selectRectangle| image:: /static/common/mActionSelectRectangle.png
   :width: 1.5em
