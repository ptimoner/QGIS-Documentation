|LS| Changing Raster Symbology
======================================================================

Não todos os dados raster são fotos aéreas. Existem muitas
outras formas de dados raster, e em muitos desses casos, é
essencial simbolizá-los para que eles se tornem
adequadamente visíveis e úteis.

**The goal for this lesson:** To change the symbology for a raster
layer.

|basic| |TY|
----------------------------------------------------------------------

#. Use o painel :guilabel:`Browser` para carregar :file:`srtm_41_19.tif`,
   localizado na pasta :file:`exercise_data/raster/SRTM/`
#. Dê zoom na extensão desta camada clicando com o botão direito sobre o
   :guilabel:`Layers panel` e selecione :guilabel:`Zoom to Layer`.

Este conjunto de dados é um *Modelo Digital de Elevação (MDE)*.
É um mapa da elevação (altitude) do terreno, permitindo-nos
ver onde estão as montanhas e os vales, por exemplo.

Enquanto cada pixel do conjunto de dados da
seção anterior continha informações de cor,
em um *MDE*, cada pixel contém valores de elevação.

Assim que o MDE for carregado, você notará que é uma representação em tons de cinza

.. figure:: img/greyscale_dem.png
   :align: center

O QGIS aplicou automaticamente um "stretch" aos valores
dos pixels da imagem para fins de visualização, e
aprenderemos mais sobre como isso funciona à medida que continuamos

|basic| |FA| Changing Raster Layer Symbology
----------------------------------------------------------------------

You have two different options to change the raster symbology:

#. Dentro da caixa de diálogo :guilabel:`Layer Properties`, clicando
   com o botão direito na camada e selecionando a opção
   :guilabel:`Properties`.
   Em seguida, vá para a guia :guilabel:`Symbology`
#. Clicando no botão |symbology| :sup:`Open the Layer Styling painel`
   justo acima do painel :guilabel:`Layers` (atalho
   :kbd:`F7`).
   Isto abrirá o painel :guilabel:`Layer Styling`, onde você
   poderá ir para a guia |symbology| :sup:`Symbology`.

Choose the method you prefer to work with.

|basic| |FA| Singleband gray
----------------------------------------------------------------------

When you load a raster file, if it is not a photo image like the ones
of the previous section, the default style is set to a grayscale
gradient.

Vamos explorar algumas das características deste renderizador.

.. figure:: img/dem_layer_properties.png
   :align: center

O :guilabel:`Color gradient` padrão está configurado como ``Black to white``,
o que significa que os valores baixos de pixel são pretos e os valores altos
são brancos.
Tente inverter essa configuração para ``White to black`` e veja os resultados.

 Muito importante é o parâmetro :guilabel:`Contrast enhancement`: por
padrão está configurado como ``Stretch to MinMax`` o que significa que os valores dos
pixels são esticados para os valores mínimo e máximo..

Look at the difference with the enhancement (left) and without (right):

.. figure:: img/enhancement.png
   :align: center

Mas quais são os valores mínimo e máximo que devem ser usados para
o esticamento?
Os que estão atualmente em
:guilabel:`Min / Max Value Settings`.
Há muitas maneiras de calcular os valores mínimo e máximo e
usá-los para o esticamento:

#. **Definido pelo usuário**: você insere os valores :guilabel:`Min` e :guilabel:`Max`
   manualmente
#. **Corte de contagem cumulativa**: isso é útil quando você tem alguns valores
   extremamente baixos ou altos. Isto *corta* os ``2%`` (ou o valor que você escolher)
   desses valores
#. **Min / max**: the *Real* or *Estimated* minimum and maximum values
   of the raster
#. **Mean +/- standard deviation**: the values will be calculated
   according to the mean value and the standard deviation


|basic| |FA| Singleband pseudocolor
----------------------------------------------------------------------

Grayscales are not always great styles for raster layers.
Let's try to make the DEM more colorful.

* Altere o :guilabel:`Render type` para
  :guilabel:`Singleband pseudocolor`.
  Se você não gostar das cores padrões carregadas, escolha uma outra
  :guilabel:`Color ramp`
* Click the :guilabel:`Classify` button to generate a new color
  classification
* If it is not generated automatically click on the :guilabel:`OK`
  button to apply this classification to the DEM

.. figure:: img/dem_pseudocolor_properties.png
   :align: center

You'll see the raster looking like this:

.. figure:: img/pseudocolor_raster.png
   :align: center

This is an interesting way of looking at the DEM.
You will now see that the values of the raster are again properly
displayed, going from blue for the lower areas to red for the higher
ones.


|FA| Alterar a Transparência
----------------------------------------------------------------------

Sometimes changing the transparency of the whole raster layer can help
you to see other layers covered by the raster itself and better
understand the study area.

Para alterar a transparência de todo o raster, mude para a guia
:guilabel:`Transparency` e use o controle deslizante da
:guilabel:`Global Opacity` para reduzir a opacidade:

.. figure:: img/global_transparency.png
   :align: center

Mais interessante é alterar a transparência de alguns valores de pixéis.
Por exemplo, no raster que utilizámos, pode ver uma cor homogénea nos
nos cantos.
Para definir estes pixéis como transparentes, vá a
:guilabel:`Custom Transparency Options` na guia
:guilabel:`Transparency`.

* Clicando no botão |symbologyAdd| :sup:`Add values manually`,
  pode adicionar um intervalo de valores e definir a sua percentagem de transparência
* Para valores individuais, o botão |contextHelp| :sup:`Add values from display`
  é mais útil
* Clique no botão |contextHelp| :sup:`Add values from display`.
  A caixa de diálogo desaparece e pode interagir com o mapa.
* Clique na cor homogénea num canto do MDE
* You will see that the transparency table will be filled with the
  clicked values:

  .. figure:: img/click_transparency.png
     :align: center

* Clique em :guilabel:`OK` para fechar a janela e ver as alterações.

  .. figure:: img/good_raster.png
     :align: center

  See? The corners are now 100% transparent.


|IC|
----------------------------------------------------------------------

Estas são algumas das funções básicas para o iniciar na simbologia
raster.
O QGIS também oferece muitas outras opções, como a simbologia de uma camada
utilizando paletas/valores únicos, representando diferentes bandas com
diferentes cores numa imagem multiespectral, ou criar um efeito
de sombra (útil apenas com raster MDE).

Reference
----------------------------------------------------------------------

The SRTM dataset was obtained from
`http://srtm.csi.cgiar.org/ <http://srtm.csi.cgiar.org/>`_

|WN|
----------------------------------------------------------------------

Now that we can see our data displayed properly, let's investigate how we can
analyze it further.


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
.. |contextHelp| image:: /static/common/mActionContextHelp.png
   :width: 1.5em
.. |symbology| image:: /static/common/symbology.png
   :width: 2em
.. |symbologyAdd| image:: /static/common/symbologyAdd.png
   :width: 1.5em
