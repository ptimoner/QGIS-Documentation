|LS| Useful QGIS Plugins
===============================================================================

Now that you can install, enable and disable plugins, let's see how this can
help you in practice by looking at some examples of useful plugins.

**The goal for this lesson:** To familiarize yourself with the plugin interface
and get acquainted with some useful plugins.


|basic| |FA| The QuickMapServices Plugin
-------------------------------------------------------------------------------

O complemento QuickMapServices é um complemento simples e fácil de usar para
adicionar mapas básicos (basemap)
para o seu projeto.
Tem muitas diferentes opções e configurações.
Exploremos algumas das possibilidades.

#. Start a new map and add the :guilabel:`roads` layer from the :file:`training_data`
   Geopackage.
#. Install the **QuickMapServices** plugin.
#. Clique em :menuselection:`Web --> QuickMapServices`.
   O primeiro menu mostra uma lista de diferentes fornecedores de mapa com mapas
   disponíveis.
#. Selecione um mapa base que você desejaria adicionar no seu projeto.

   .. figure:: img/qms_result.png
      :align: center
      :width: 80%

Ótimo! Mas uma das ventagens principais do QMS é que da um acesso a muitos fornecedores de dados.
Vamos adicioná-los.

#. Clique em :menuselection:`Web --> QuickMapServices --> Settings`
#. Vá para a guia :guilabel:`More services`.
#. Read carefully the message of this tab and if you agree click on the
   :guilabel:`Get Contributed pack` button.
#. Clique :guilabel:`Save`.

#. Abra de novo o menu :menuselection:`Web --> QuickMapServices` e você verá
   que mais fornecedores de dados estão disponíveis.

   .. figure:: img/qms_menu.png
      :align: center

#. Escolhe algum mapa, e carregue os dados no seu
projeto!

Também é possivel pesquisar a través dos novos fornecedores de dados.

#. Abra a aba de pesquisa clicando em :menuselection:`Web --> QuickMapServices --> Search QMS`.
   Esta opção do complemento permite filtrar os mapas básicos em função da 
   extenção da sua tela de mapa ou usando palavras chaves.
#. Clique em :guilabel:`Filter by extent` e deveria ver um serviço disponível.
   Se não tiver nenhum, diminui o zoom e percorra o mapa
   ou pesquise usando palavras chaves.
#. Clique no botão :guilabel:`Add` para carregar os dados.
#. O mapa base será carregado e você terá uma camada de fundo para seu mapa

   .. figure:: img/qms_search_added.png
      :align: center
      :width: 80%


|basic| |FA| The QuickOSM Plugin
-------------------------------------------------------------------------------

With an incredible simple interface, the QuickOSM plugin allows you to download
`OpenStreetMap <https://www.openstreetmap.org/>`_ data.

#. Start a new empty project and add the :guilabel:`roads` layer from the
   :file:`training_data` GeoPackage.
#. Install the **QuickOSM** plugin.
   The plugin adds two new buttons in the QGIS Toolbar
   and is accessible in the :menuselection:`Vector --> QuickOSM` menu.
#. Open the QuickOSM dialog. The plugin has many different tabs: we will use the
   :guilabel:`Quick Query` one.
#. You can download specific features by selecting a generic :guilabel:`Key` or be more
   specific and choose a specific :guilabel:`Key` and :guilabel:`Value` pair.

   .. tip:: if you are not familiar with the :guilabel:`Key` and :guilabel:`Value`
    system, click on the :guilabel:`Help with key/value` button. It will open a
    web page with a complete description of this concept of OpenStreetMap.

#. Pesquise :guilabel:`railway` no menu :guilabel:`Key` e deixa :guilabel:`Value`
   vazío: então estamos baixando todas as feições :guilabel:`railway` sem
   especificar nehum valor.
#. Select :guilabel:`Layer Extent` in the next drop-down menu and choose :guilabel:`roads`.
#. Click on the :guilabel:`Run query` button.

   .. figure:: img/quickosm_setup.png
      :align: center

After some seconds the plugin will download all the features tagged in OpenStreetMap
as ``railway`` and load them directly into the map.

Nothing more! All the layers are loaded in the legend and are shown in the map
canvas.

.. figure:: img/quickosm_result.png
   :align: center
   :width: 60 %

.. warning:: QuickOSM creates temporary layer when downloading the data. If you
  want to save them permanently, click on the |indicatorMemory| icon next to the
  layer and choose the options you prefer. Alternatively you can open the
  :kbd:`Advanced` menu in QuickOSM and choose where to save the data in the
  :guilabel:`Directory` menu.


|IC|
-------------------------------------------------------------------------------

There are many useful plugins available for QGIS. Using the built-in tools for
installing and managing these plugins, you can find new plugins and make
optimum use of them.


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
.. |addHtml| image:: /static/common/mActionAddHtml.png
   :width: 1.5em
.. |basic| image:: /static/common/basic.png
.. |hard| image:: /static/common/hard.png
.. |helpContents| image:: /static/common/mActionHelpContents.png
   :width: 1.5em
.. |indicatorMemory| image:: /static/common/mIndicatorMemory.png
   :width: 1.5em
.. |saveMapAsImage| image:: /static/common/mActionSaveMapAsImage.png
   :width: 1.5em
.. |symbology| image:: /static/common/symbology.png
   :width: 2em
