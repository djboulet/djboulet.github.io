
Gasoline Price Compare
^^^^^^^^^^^^^^^^^^^^^^^^^

Background
""""""""""""""

Comparing the unit price of a commodity with different units of measure
and currencies is greatly simplified with a nomograph.  In this example,
cross-border travellers between the United States and Canada can easily
compare the cost of gasoline (petrol) on both sides of the border.  Moreover, by
drawing an isopleth through the currency rate at par (1.0000) they can
directly convert dollars per litre to dollars per USG.  This nomograph
implements the following formula:

:Math:`\frac{CAD}{L} =  \frac{CAD}{USD} \times \frac{USD}{US Gal} \div \frac{L}{US Gal}`

This equation follows the form of a **Type 2** nomograph where:

:math:`F_1(u_1) = \frac{CAD}{L}`,

:math:`F_2(u_2) = \frac{CAD}{USD}`

and

:math:`F_3(u_3) = \frac{USD}{US Gal} \div 3.78541 \frac{L}{US Gal}`

Generated nomograph
""""""""""""""""""""""


.. image:: ../../../../mynomos/gasolinepricesUSD_CAD.png



Source code
-----------


.. literalinclude:: ../../../../mynomos/gasolinepricesUSD_CAD.py
    :encoding: latin-1
    :linenos:
    :lines: 1-4, 20-

