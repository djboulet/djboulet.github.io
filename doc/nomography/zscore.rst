Z score calculator
^^^^^^^^^^^^^^^^^^^^^^^^^^

Theory and background
"""""""""""""""""""""""

This example extends Pynomo’s versatility by using external libraries.
Python’s :code:`scipy` library is the engine behind this nomograph
which calculates the area under a normal distribution curve between
two Z scores (one negative, the other positive).

To calculate the area between two Z scores (:math:`Z_{upper}`,
:math:`Z_{lower}`) of a normal distribution one must compute the
difference between the respective probability density functions
:math:`\mathrm{PDF}(Z_{upper})` and :math:`\mathrm{PDF}(Z_{lower})`. :cite:`wikimedia:normal_disribution`

.. image:: The_Normal_Distribution.png


Recall that the functional relationship for a **Type 1** block is:

:math:`F1(u_1)+F2(u_2)+F3(u_3)=0`

and

:math:`\mathrm{Area} = \mathrm{PDF}(Z_{upper}) - \mathrm{PDF}(Z_{lower})`

therefore

:math:`\mathrm{PDF}(Z_{upper})  - Area  - \mathrm{PDF}(Z_{lower})=0`.

Two **Type 8** axes are aligned with :math:`\mathrm{PDF}(Z_{upper})` and
:math:`\mathrm{PDF}(Z_{lower})` to align a Z score with its associated PDF.


Nomograph
"""""""""

.. image:: ../../../mynomos/ghpage_src/zscore.png

Source code
"""""""""""

.. literalinclude:: ../../../mynomos/ghpage_src/zscore.py
    :encoding: latin-1
    :linenos:
    :lines: 1-4, 20-

