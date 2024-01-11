|LS| Using Print Layout
======================================================================

Agora que você tem um mapa, é necessário ser capaz de imprimir ou
exportá-lo para um documento.
A razão disso é que um arquivo de mapa GIS não é uma imagem. Em vez disso, ele salva o
estado do programa GIS, com referências a todas as camadas, suas
etiquetas, cores, etc.
Então, para alguém que não tem os dados ou o mesmo programa GIS
(como o QGIS), o arquivo de mapa será inútil.
Felizmente, o QGIS pode exportar seu arquivo de mapa para um formato que qualquer
computador pode ler, além de imprimir o mapa se você tiver uma
impressora conectada.
Tanto a exportação quanto a impressão são gerenciadas através do *Print Layout*.

**Objetivo desta lição:** Usar o *Print Layout* do QGIS para criar
um mapa básico com todas as configurações necessárias.

|basic| |FA| The Layout Manager
----------------------------------------------------------------------

O QGIS permite que você crie múltiplos mapas usando o mesmo arquivo de mapa.
Por essa razão, ele possui uma ferramenta chamada *Layout Manager*.

#. Clique na entrada do menu :menuselection:`Project --> Layout Manager...` 
   para abrir esta ferramenta.
   Você verá um diálogo :guilabel:`Layout manager` em branco aparecer.

   .. figure:: img/layout_manager_dialog.png
      :align: center

#. Em :guilabel:`New from Template`, selecione
   :guilabel:`Empty layout` e pressione o botão :guilabel:`Create...`.
#. Dê ao novo layout o nome de |majorUrbanName| ed
   clique em :guilabel:`OK`.
#. You will now see the *Print Layout* window:

   .. figure:: img/print_composer_dialog.png
      :align: center
   
Você também poderia criar este novo layout através do menu
:menuselection:`Project --> New Print Layout...`.

Independentemente do caminho que você escolher, o novo layout de impressão agora está
acessível a partir do menu :menuselection:`Project --> Layouts -->`, conforme a imagem abaixo.

.. figure:: img/print_composer_menu.png
   :align: center


|basic| |FA| Basic Map Composition
----------------------------------------------------------------------

In this example, the composition was already the way we wanted it.
Ensure that yours is as well.

#. Clique com o botão direito na folha na parte central da janela de layout
   e escolha :guilabel:`Page properties...` no menu de contexto.
#. Verifique se os valores na aba :guilabel:`Item Properties` estão
   configurados da seguinte forma:

   * :guilabel:`Size`: ``A4``
   * :guilabel:`Orientation`: ``Landscape``

   Now you've got the page layout the way you wanted it, but this
   page is still blank.
   It clearly lacks a map. Let's fix that!

#. Clique no botão |addMap| :sup:`Add Map`.

   With this tool activated, you will be able to place a map on the
   page.

#. Click and drag a box on the blank page:

   .. figure:: img/drag_add_map.png
      :align: center

   The map will appear on the page.

#. Move the map by clicking and dragging it around:

   .. figure:: img/move_map.png
      :align: center

#. Resize it by clicking and dragging the boxes on the edges:

   .. figure:: img/resize_map.png
      :align: center

   .. note::  Your map may look a lot different, of course!
      This depends on how your own project is set up.
      But not to worry! These instructions are general, so they will
      work the same regardless of what the map itself looks like.

#. Be sure to leave margins along the edges, and a space along the
   top for the title.

#. Zoom in and out on the page (but not the map!) by using these
   buttons:

   |zoomFullExtent| |zoomIn| |zoomOut|

#. Amplie e mova o mapa na janela principal do QGIS.
   Você também pode mover o mapa usando a ferramenta |moveItemContent|
   :sup:`Move item content`.

   The map view updates as you zoom in or zoom out.
#. Se, por algum motivo, a visualização do mapa não atualizar corretamente,
   você pode forçar a atualização do mapa clicando no botão
   |refresh| :sup:`Refresh view`.

   Lembre-se de que o tamanho e a posição que você deu ao mapa não precisam
   ser finais.
   Você sempre pode voltar e alterá-los mais tarde se não estiver
   satisfeito. 
   Por enquanto, certifique-se de ter salvo seu trabalhoneste mapa.
   Como um *Print Layout* no QGIS faz
   parte do arquivo principal do mapa, 
   você deve salvar o seu projeto.

#. Vá para :menuselection:`Layout -->` |fileSave|
   :menuselection:`Save Project`.
   Este é um atalho conveniente para o da caixa de diálogo principal.

|basic| |FA| Adding a Title
----------------------------------------------------------------------

Now your map is looking good on the page, but your readers/users are
not being told what's going on yet.
They need some context, which is what you'll provide for them by
adding map elements.
First, let us add a title.

#. Clique no botão |label| :sup:`Add Label`
#. Clique na página, acima do mapa, aceite os valores sugeridos na caixa
   de diálogo :guilabel:`New Item Properties`, e uma etiqueta aparecerá
   no topo do mapa.
#. Resize it and place it in the top center of the page.
   It can be resized and moved in the same way that you resized and
   moved the map.

   As you move the title, you'll notice that guidelines appear to
   help you position the title in the center of the page.

   Entretanto, há também uma ferramenta na Barra de Ferramentas de Ações 
   para ajudar a posicionar o título em relação ao mapa (não à página):

   |alignLeft|

#. Click the map to select it
#. Hold in :kbd:`Shift` on your keyboard and click on the label so
   that both the map and the label are selected.
#. Procure o botão |alignLeft| :sup:`Align selected items left`
   e clique na seta suspensa ao lado dele para revelar as opções de 
   posicionamento e clique |alignHCenter|
   :guilabel:`Align center`:

   .. figure:: img/align_center_dropdown.png
      :align: center

   Now the label frame is centered on the map, but not the contents.
   To center the contents of the label:

   #. Select the label by clicking on it.
   #. Clique na guia :guilabel:`Item Properties` no painel lateral
      da janela de layout.
   #. Change the text of the label to "|majorUrbanName|":

      .. figure:: img/title_font_alignment.png
         :align: center

   #. Use essa interface para definir as opções de fonte e alinhamento
      na seção :guilabel:`Appearance`:

      #. Escolha uma fonte grande, mas sensível (o exemplo
         usará a fonte padrão com tamanho ``36``)
      #. Set the :guilabel:`Horizontal Alignment` to :guilabel:`Center`.

      You can also change the font color, but it's probably best to
      keep it black as per the default.

   #. The default setting is not to add a frame to the title's text box.
      However, if you wish to add a frame, you can do so:

      #. In the :guilabel:`Item Properties` tab, scroll down until you
         see the :guilabel:`Frame` option.
      #. Click the :guilabel:`Frame` checkbox to enable the frame.
         You can also change the frame's color and width.

   In this example, we won't enable the frame, so here is our page so
   far:

   .. figure:: img/page_so_far.png
      :align: center

   To make sure that you don't accidentally move these elements
   around now that you've aligned them, you can lock items into place:

   #. Select both the label and the map items
   #. Clique no botão |lockItems| :sup:`Lock Selected Items` na
      barra de ferramentas *Actions*.

      .. note:: Clique no botão |unlockAll| :sup:`Unlock All Items`
       na barra de ferramentas *Actions* para poder editar os itens novamente.


|basic| |FA| Adding a Legend
----------------------------------------------------------------------

The map reader also needs to be able to see what various things on
the map actually mean.
In some cases, like the place names, this is quite obvious.
In other cases, it's more difficult to guess, like the colors of the
forests.
Let's add a new legend.

#. Click on the |addLegend| :sup:`Add Legend` button
#. Clique na página para colocar a legenda, aceite os valores sugeridos
   na caixa de diálogo :guilabel:`New Item Properties`,
#. A legend is added to the layout page, showing layers symbology
   as set in the main dialog.
#. As usual, you can click and move the item to where you want it:

   .. figure:: img/legend_added.png
      :align: center
      :width: 100%

|moderate| |FA| Customizing Legend Items
----------------------------------------------------------------------

Not everything on the legend is necessary, so let's remove some
unwanted items.

#. Na guia :guilabel:`Item Properties`, você encontrará o grupo
   :guilabel:`Legend items`.
#. Desmarque a caixa |unchecked| :guilabel:`Auto update`, permitindo
   que você modifique diretamente os itens da legenda.
#. Select the entry with :guilabel:`buildings`
#. Apague isso da legenda clicando no botão |symbologyRemove|

You can also rename items.

#. Select a layer from the same list.
#. Clique no botão |symbologyEdit| :sup:`Edit selected item properties`.
#. Renomeie as camadas para ``Places``, ``Roads and Streets``,
   ``Surface Water``, and ``Rivers``.

You can also reorder the items:

.. figure:: img/categories_reordered.png
   :align: center
   :width: 100%

As the legend will likely be widened by the new layer names, you may
wish to move and resize the legend and or map.
This is the result:

.. figure:: img/map_composer_result.png
   :align: center
   :width: 100%

|basic| |FA| Exporting Your Map
----------------------------------------------------------------------

.. note::  Did you remember to save your work often?

Finally the map is ready for export! You'll see the export buttons
near the top left corner of the layout window:

* |filePrint| :sup:`Print Layout`: interfaces with a printer.
  Como as opções de impressora podem variar dependendo do modelo da
  impressora com a qual você está trabalhando, provavelmente é melhor
  consultar o manual da impressora ou um guia geral de impressão
  para obter mais informações sobre esse tópico."

  The other buttons allow you to export the map page to a file.
* |saveMapAsImage| :sup:`Export as Image`: Fornece uma seleção de
  vários formatos comuns de imagem para escolher.
  Esta é provavelmente a opção mais simples, mas a imagem que cria é
  "fixa"" e difícil de editar.
* |saveAsSVG| :sup:`Export as SVG`: Se você estiver enviando o mapa para
  um cartógrafo (que pode querer editar o mapa para publicação), é melhor
  exportar como SVG. SVG significa 'Scalable Vector Graphic'
  (Gráfico Vetorial Escalável) e pode ser importado para programas como o
  `Inkscape <https://inkscape.org/>`_ ou outros softwares de edição de imagens vetoriais.
* |saveAsPDF| :sup:`Export as PDF`: Se você precisar enviar o mapa para um cliente,
  é mais comun utilzar um PDF, porque é mais fácil configurar as opções
  de impressão para um PDF. Alguns cartógrafos também podem preferir o PDF
  si tiverem um programa que lhes permita importar e editar este formato.

For our purposes, we're going to use PDF.

#. Click the |saveAsPDF| :sup:`Export as PDF` button
#. Escolha um local de salvamento e um nome de arquivo como de costume.
   A seguinte caixa de diálogo aparecerá.

   .. figure:: img/layout_export_pdf.png
      :align: center
   
#. You can safely use the default values now and click
   :guilabel:`Save`.
   
   QGIS will proceed to the map export and push a message
   on top of the print layout dialog as soon as it finishes.
#. Clique no hiperlink na mensagem para abrir a pasta na qual o PDF
   foi salvo no gerenciador de arquivos do seu sistema.
#. Open it and see how your layout looks.

   Everything is OK?
   Congratulations on your first completed QGIS map project!

#. Anything unsatisfying? Go back to the QGIS window, do the
   appropriate modifications and export again.
#. Remember to save your project file.


|IC|
----------------------------------------------------------------------
Agora você sabe como criar um layout básico de mapa.


.. Substitutions definitions - AVOID EDITING PAST THIS LINE
   This will be automatically updated by the find_set_subst.py script.
   If you need to create a new substitution manually,
   please add it also to the substitutions.txt file in the
   source folder.

.. |FA| replace:: Siga o Passo a Passo:
.. |IC| replace:: Em Conclusão
.. |LS| replace:: Lição:
.. |WN| replace:: O Que Vem a Seguir?
.. |addLegend| image:: /static/common/mActionAddLegend.png
   :width: 1.5em
.. |addMap| image:: /static/common/mActionAddMap.png
   :width: 1.5em
.. |alignHCenter| image:: /static/common/mActionAlignHCenter.png
   :width: 1.5em
.. |alignLeft| image:: /static/common/mActionAlignLeft.png
   :width: 1.5em
.. |basic| image:: /static/common/basic.png
.. |filePrint| image:: /static/common/mActionFilePrint.png
   :width: 1.5em
.. |fileSave| image:: /static/common/mActionFileSave.png
   :width: 1.5em
.. |label| image:: /static/common/mActionLabel.png
   :width: 1.5em
.. |lockItems| image:: /static/common/mActionLockItems.png
   :width: 1.5em
.. |majorUrbanName| replace:: Swellendam
.. |moderate| image:: /static/common/moderate.png
.. |moveItemContent| image:: /static/common/mActionMoveItemContent.png
   :width: 1.5em
.. |refresh| image:: /static/common/mActionRefresh.png
   :width: 1.5em
.. |saveAsPDF| image:: /static/common/mActionSaveAsPDF.png
   :width: 1.5em
.. |saveAsSVG| image:: /static/common/mActionSaveAsSVG.png
   :width: 1.5em
.. |saveMapAsImage| image:: /static/common/mActionSaveMapAsImage.png
   :width: 1.5em
.. |symbologyEdit| image:: /static/common/symbologyEdit.png
   :width: 1.5em
.. |symbologyRemove| image:: /static/common/symbologyRemove.png
   :width: 1.5em
.. |unchecked| image:: /static/common/unchecked.png
   :width: 1.3em
.. |unlockAll| image:: /static/common/mActionUnlockAll.png
   :width: 1.5em
.. |zoomFullExtent| image:: /static/common/mActionZoomFullExtent.png
   :width: 1.5em
.. |zoomIn| image:: /static/common/mActionZoomIn.png
   :width: 1.5em
.. |zoomOut| image:: /static/common/mActionZoomOut.png
   :width: 1.5em
