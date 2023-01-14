True VSWR Calculator
^^^^^^^^^^^^^^^^^^^^^^^^

Introduction
"""""""""""""""

Amateur radio operators frequently design and build their own antennae.  An important performance 
characteristic of any antenna system is the **Voltage Standing Wave Ratio** (VSWR).  The VSWR is a
measure of the impedance match between the signal source (transmitter) and the load (antenna). Maximum
power transfer from transmitter to antenna occurs when the source's output impedance matches the load's
input impedance. A VSWR of 1:1 or simply "1" indicates a perfect match.

VSWR, Return Loss and Cable Attentuation
"""""""""""""""""""""""""""""""""""""""""""""

The VSWR is calculated from the forward and reflected power as follows :cite:`enwiki:1061732394`:

:math:`VSWR = \frac{1+\sqrt{P_r/P_f}}{1-\sqrt{P_r/P_f}}`.

**Return loss** (RL) is also an indicator of antenna performance. It is the ratio of forward power to
 reflected power expressed in decibels (dB) :cite:`electronicnotes_2021`:

:math:`RL = 10 \log_{10}{P_\mathrm f \over P_\mathrm r}`

where :math:`P_f` and :math:`P_r` are respectively forward and reflected power in Watts.  By converting forward
 and reflected power readings to a decibel value referenced to 1W (0 dBW) the return loss can be expressed as:

:math:`RL = P_f - P_r` (dB)

Return loss and VSWR are related :cite:`electronicnotes_2021` by the following formulae:

:math:`RL = -20 \times \log_{10} \frac{VSWR - 1}{VSWR + 1}`

and

:math:`VSWR = \frac{10^\frac{RL}{20} + 1}{10^\frac{RL}{20} - 1}`.


A high return loss (>30dB) indicates a high ratio of forward power to reflected power therefore 
a good impedance match. A return loss approaching 0dB means 
the reflected power is nearly equal to the forward power indicating a mismatch.

Cable loss and impact on VSWR
""""""""""""""""""""""""""""""""""

VSWR is a useful indicator of power transfer but measured results can be misleading.
The transmission line connecting the transmitter to the antenna will introduce some loss therefore
the RF power reaching the antenna will be lower than the RF power 
delivered by the transmitter.  Similarly, the power reflected by the antenna will 
also have been attenuated by the transmission line before it returns 
to the power meter. The combined effect of attenuated forward and reflected power 
will make it appear as though the VSWR is lower than it would be if 
measured at the antenna. It isn't practical to install a power meter at the antenna but the 
true VSWR can be calculated based on measured VSWR and known cable losses.

Cable attenuation is specified in dB per unit length. Cable attentuation for LMR®-195 is based on the following formula :cite:`timesmicrowave:lmr195`:

:math:`Loss = (0.356859) \times \sqrt{f} + (0.000470) \times f`

where :math:`Loss` is the attentuation per 100 feet and :math:`f` is the operating frequency in megahertz. Given forward and reflected power readings in dB and cable length, we can easily calculate the true return loss at the antenna:

:math:`RL_{true} = RL_{measured} - 2 * Loss`.

A return loss figure can then be converted to VSWR using the formula described earlier.

Nomograph construction
"""""""""""""""""""""""""""""

Both formulae for return loss can be easily put into a form acceptable for Type 1 block.   A graph is created using a Type 5 nomograph to calculate cable losses given a length and operating frequency.

Since radio amateurs usually work in terms of power expressed in Watts and VSWR, Type 8 blocks are anchored to the Type 1 blocks to convert dbW and RL into Watts and VSWR respectively.  The dB axes are hidden to minimize clutter.




 
Generated nomograph
""""""""""""""""""""""""""""""

.. image:: ../../../mynomos/true_vswr_lmr400.png


Source code
"""""""""""""""""

.. literalinclude:: ../../../mynomos/true_vswr_lmr400.py
    :encoding: latin-1
    :linenos:
    :lines: 1-4, 20-

