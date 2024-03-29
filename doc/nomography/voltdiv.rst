Voltage Divider
^^^^^^^^^^^^^^^^^^^^^

Theory and background
"""""""""""""""""""""""

In electronics, resistive voltage dividers are used for a variety of purposes.
The formula for a resistive voltage divider is :cite:`wiki:Voltage_divider`:

:math:`\frac{V_{out}}{V_{in}} = \frac{R_b}{(R_a + R_b)}``

.. image:: voltage_divider_schematic.png
   :width: 200

When designing voltage dividers, constraints may demand engineers choose
resistors from a set of “preferred values” :cite:`wiki:E_series_of_preferred_numbers`. These values are
discrete and engineers must select the best combination of resistors
based on tolerance and the available preferred values.  Similar voltage
ratios can be obtained with different combinations of resistor values.

The voltage divider nomograph links input voltage (:math:`V_{in}`), output voltage (:math:`V_{out}`) and a
pair of resistor values into a single nomograph.  Pynomo’s **Type 5** blocks
are well suited for plotting relationships between pairs of discrete values.
A vertical line dropped from the intersection of :math:`R_a` values and :math:`R_b` values
reveals the :math:`V_{out}` / :math:`V_{in}` voltage ratio.  Alignment with a **Type 2** block allows
the engineer to determine :math:`V_{out}` given :math:`V_{in}` (or vice versa).

Of greater benefit is the ability to quickly determine the optimum pair
of resistor values for a given application.  For example, given an input
voltage (9V) and desired output voltage (3.3V), the engineer draws a straight
line from the :math:`V_{out}` axis, through the :math:`V_{in}` axis to the base of the voltage ratio
graph.  A perpendicular line is then drawn from the base to the top of the
graph.  The vertical line’s nearest approach to the intersection of the horizontal :math:`R_a` and curved
:math:`R_b` lines represents the best combination of resistor values.  It can be
quickly shown that one combination of values (:math:`R_a` = 6.2 and :math:`R_b` = 3.6) will
produce an output voltage very close to the desired value (3.3061V).

Nomograph
"""""""""

.. image:: ../../../mynomos/ghpage_src/voltdiv_E24_resistors.png

Source code
"""""""""""

.. literalinclude:: ../../../mynomos/ghpage_src/voltdiv_E24_resistors.py
    :encoding: latin-1
    :linenos:
    :lines: 1-4, 20-

