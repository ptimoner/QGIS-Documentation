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

Para calcular o declive, você precisa utilizar o algoritmo :menuselection:`Slope`
em :menuselection:`Processing --> Raster terrain analysis`.

#. Open the algorithm
#. Selecione :guilabel:`srtm_41_19` como :guilabel:`Elevation layer`
#. Mantém o :guilabel:`Z factor` em ``1.0``
#. Salve o resultado como arquivo nomeado ``slope`` na mesma pasta que a camada
   ``hillshade``
#. Click on :guilabel:`Run`

Agora verá o declive do terreno, cada pixel com o valor de declive correspondente. Os pixéis pretos mostram um terreno plano e os pixéis brancos, um terreno íngreme:

.. figure:: img/slope_raster.png
   :align: center


|moderate| |TY| Calculando o Aspecto (Orientação das Vertentes)
----------------------------------------------------------------------

O *aspecto* é a direção da bússola para a qual a inclinação do terreno está virada. Um aspeto de 0 significa que a inclinação está virada para Norte,
90 virado para Leste, 180 virado para Sul e 270 virado para Oeste.

Since this study is taking place in the Southern Hemisphere, properties should
ideally be built on a north-facing slope so that they can remain in the
sunlight.

Use o algoritmo :guilabel:`Aspect` em
:menuselection:`Processing --> Raster terrain analysis` para obter uma camada 
``aspect``salvada juntamente com a camada ``slope``.

.. admonition:: Answer
   :class: dropdown

   Defina a caixa de diálogo :guilabel:`Aspect` desse jeito:

   .. figure:: img/answer_dem_aspect.png
      :align: center

   Your result:

     .. figure:: img/answer_aspect_result.png
        :align: center


|moderate| |FA| Reclassificar o Raster
----------------------------------------------------------------------

Sabemos agora que tem valores numéricos num intervalo de 0 a 360.

O que queremos é *reclassificar* esta camada para outros valores discretos
(de 1 a 4), dependendo do aspecto:

* 1 = North (from 0 to 45 and from 315 to 360);
* 2 = East (from 45 to 135)
* 3 = South (from 135 to 225)
* 4 = West (from 225 to 315)

This operation can be achieved with the raster calculator, but the
formula would become very very large.

A ferramenta alternativa é algoritmo :guilabel:`Reclassify by table`
em :menuselection:`Raster analysis` no
:guilabel:`Processing Toolbox`.

#. Open the tool
#. Escolhe :guilabel:`aspect` como ``Input raster layer``
#. Clique em :guilabel:`...` do :guilabel:`Reclassification table`.
   Aparece uma caixa de diálogo semelhante a uma tabela, onde pode escolher os
   valores mínimo, máximo e novo para cada classe.
#. Click on the :guilabel:`Add row` button and add 5 rows.
   Fill in each row as the following picture and click :guilabel:`OK`:

   .. figure:: img/reclassify_table.png
      :align: center

#. Salve a camada as :file:`reclassified.tif` na pasta
   :file:`exercise_data/raster_analysis/`

   .. figure:: img/reclassify_setup.png
      :align: center

#. Click on :guilabel:`Run`

Se compararmos a camada original :guilabel:`aspect` com a camada
:guilabel:`reclassified`, não existem grandes diferenças. Mas ao olhar para a
legenda, pode ver que os valores vão de
``1`` to ``4``.

Let us give this layer a better style.

#. Abra o painel the :guilabel:`Layer Styling`
#. Selecione :guilabel:`Paletted/Unique values`, em vez de
   :guilabel:`Singleband gray`
#. Clique no botão :guilabel:`Classify` para obter automaticamente
   os valores e atribuir-lhes cores aleátorias:

   .. figure:: img/unique_style.png
      :align: center

The output should look like this (you can have different colors given
that they have been randomly generated):

.. figure:: img/reclassify_result.png
   :align: center

Com esta reclassificação e o estilo de paleta aplicado à camada, é possível 
diferenciar imediatamente as áreas de aspecto.


|basic| |FA| Consultar o raster
----------------------------------------------------------------------

Ao contrário das camadas vectoriais, as camadas raster não
têm uma tabela de atributos. Cada pixel contém um ou mais valores
numéricos (rasters de banda única ou raster de banda única ou multibanda).

Todas as camadas raster que utilizámos neste exercício consistem apenas numa banda. Dependendo da camada, os valores de pixel podem
representar valores de elevação, aspeto ou declive.

Como podemos consultar o raster para obter o valor de um pixel?
Podemos utilizar o botão |identify| :sup:`Identify Features`!

#. Select the tool from the Attributes toolbar.
#. Clique numa localização aleatória da camada :guilabel:`srtm_41_19`.
   :guilabel:`Identify Results` aparecerá com o valor da banda no
   pixel clicado:

   .. figure:: img/identify_raster.png
      :align: center

#. Você pode alterar o resultado do painel :guilabel:`Identify Results`
   do modo atual ``tree`` para o modo ``table`` selecionando
   :guilabel:`Table` no menu :guilabel:`View` na parte inferior do
   painel:

   .. figure:: img/identify_raster_table.png
      :align: center

Clicando em cada pixel para obter o valor do raster pode ser
cansativo depois de um tempo.
Podemos utilizar o plugin (complemento) *Value Tool* para resolver este problema.

#. Go to :menuselection:`Plugins --> Manage/Install Plugins...`
#. Na guia :guilabel:`All`, digite ``value t`` na caixa de pesquisa.
#. Selecione o plugin *Value Tool*, pressione :guilabel:`Install Plugin`
   e depois no botão :guilabel:`Close` para fechar a janela.

   .. figure:: img/value_tool.png
      :align: center

   O novo painel :guilabel:`Value Tool` aparecerá.

   .. tip:: Si você fechar o painel, poderá abri-lo novamente em
      :menuselection:`View --> Panels --> Value Tool` ou clicando
      no ícone na barra de ferramentas.

#. Para utilizar o plugin certifique-se que a caixa :guilabel:`Enable` esteja
   ativada assim como a camada ``srtm_41_19`` no painel
   :guilabel:`Layers`.
#. Move the cursor over the map to see the value of the pixels.

   .. figure:: img/value_tool_query.png
      :align: center

#. Mas tem mais!
   O plugin Value Tool plugin permite consultar **todos** os raster que
   estão ativos no painel :guilabel:`Layers`.
   Ative as camadas :guilabel:`aspect` e :guilabel:`slope`
   e move o cursor sobre o mapa:

   .. figure:: img/value_tool_query_multi.png
      :align: center


|IC|
----------------------------------------------------------------------

Você viu como derivar o MDE para obter o relevo sombreado, o declive e o
aspecto. No final também aprendeu como reclassificar uma camada e consultar
os valores dos raster.

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
