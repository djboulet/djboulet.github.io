Map Romer
^^^^^^^^^^^^^^^^^^^^^

Strictly speaking, this not a nomograph.  I used PyNomo's axis drawing functions to create a 
custom `map romer <https://en.wikipedia.org/wiki/Romer>`_ to use on printed maps that don't have 
a standard scale (i.e. 1:25000).  The only constraint is that the map's 
grid must have the same scale vertically and horizontally. 
Substitute values for actual and printed grids sizes to produce a useful map romer. 

Nomograph
"""""""""

.. image:: ../../../mynomos/ghpage_src/romer.png

Source code
"""""""""""

.. literalinclude:: ../../../mynomos/ghpage_src/romer.py
    :encoding: latin-1
    :linenos:
    :lines: 1-4, 20-

