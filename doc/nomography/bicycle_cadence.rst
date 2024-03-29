Bicycle Cadence
^^^^^^^^^^^^^^^^^^

Theory and background
""""""""""""""""""""""

Choosing the correct gears on a bicycle allows a cyclist to maintain a comfortable cadence.  A higher
cadence helps reduce muscle fatigue :cite:`trainingpeaks_2021` though it does put more stress on heart and
lungs.  On the other hand a lower cadence for the same power output puts more stress on the rider's knees,
hips and back. :cite:`the_body_mechanic_2021` Furthermore, cycling cadence will vary widely with beginning cyclists peddling more
slowly (60-85 rpm) and professionals exceeding 100 rpm under certain conditions.
Generally, a good cadence in cycling is between 80-100 rpm. :cite:`hurley_cycling_2021` The
correct gear ratio can help the rider maximize their speed with a comfortable cadence.

A bicycle’s speed is the product of the wheel diameter (e.g. 700mm), 
the wheel’s rotation rate (in rpm) and :math:`\pi`. The wheel’s rotation rate is a function of
the rider’s cadence and the front to rear gear ratio. As in the previous example, pairs
of discrete values such as the number of teeth on the front and rear sprockets are
easily represented on a **Type 5** block.  This nomograph combines a **Type 5** block (to 
calculate gearing ratio) with a pair of **Type 2** blocks to calculate the rider's 
speed given their cadence and gear settings.


Nomograph
"""""""""

.. image:: ../../../mynomos/ghpage_src/bicycle_cadence.png

Source code
"""""""""""

.. literalinclude:: ../../../mynomos/ghpage_src/bicycle_cadence.py
    :encoding: latin-1
    :linenos:
    :lines: 1-4, 20-


