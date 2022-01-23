======================
HP35s / HP12c Programs
======================

:Author: Daniel J Boulet

.. raw:: latex

   \thispagestyle{empty}

.. raw:: latex

   \maketitle

.. raw:: latex

   \newpage 

.. raw:: latex

   \thispagestyle{empty}

Revision History
================

+-----------------------------------+-----------------------------------+
| **Revision Date**                 | **Description**                   |
+===================================+===================================+
| May 25, 2016                      | Revised *Modular Exponentiation   |
|                                   |  program by using DSE function    |
|                                   | instead of direct variable        |
|                                   | count.*                           |
+-----------------------------------+-----------------------------------+
| June 26, 2021                     | Renamed *Modular Exponentiation   |
|                                   |  to modexp.*                      |
+-----------------------------------+-----------------------------------+
|                                   | Added blank pages for double      |
|                                   | sided printing.                   |
+-----------------------------------+-----------------------------------+
|                                   | Added program to calculate actual |
|                                   | VSWR based on measured VSWR and   |
|                                   | cable loss.                       |
+-----------------------------------+-----------------------------------+

.. raw:: latex

   \pagebreak

.. raw:: latex

   \newpage 

.. raw:: latex

   \thispagestyle{empty}

.. raw:: latex

   \tableofcontents

.. raw:: latex

   \newpage 

.. raw:: latex

   \setcounter{page}{1}

HP35s
=====

modexp
------

.. raw:: latex

   \setcounter{hppgline}{0}

Description
~~~~~~~~~~~

This program calculates the modulus of a number raised to a large power.
The formula looks like this:

.. math:: {modexp} = n^p\ \bmod m

Usage
^^^^^

``GTO A001 n R/S p R/S m R/S``

Program Listing
~~~~~~~~~~~~~~~

R1.25cm L2.5cm L10.0cm

| & ``LBL A`` &start of program
| & ``STO N`` &store number to the raised to the power P
| & ``STOP`` &wait for user R/S
| & ``STO P`` &store exponent
| & ``STOP`` &wait for user R/S
| & ``STO M`` &store modulus
| & ``1`` &initialize product ...
| & ``STO R`` &... and save in memory
| & ``RCL N`` &recall base ...
| & ``RCL R`` &recall product ...
| & ``\times`` &... and multiply the two
| & ``RCL M`` &recall the modulus ...
| & ``RMDR`` &... and apply it
| & ``STO R`` &save the new product
| & ``DSE P`` &decrement exponent ...
| & ``GTO A009`` &... and loop back if not finished.
| & ``RCL R`` &pull the product from memory
| & ``RTN`` &we are done!

Example
~~~~~~~

In the following example we calculate :math:`\mathbf{5^{101} \bmod 31}`
using the following steps: ``GTO A001`` ``0.00000`` ``5 R/S``
``5.00000`` ``101 R/S`` ``101.00000`` ``31 R/S`` ``25.00000``

Comments
~~~~~~~~

The HP35s is not known for it’s lightning speed. The above example will
take about 12 seconds to run.

atan2
-----

.. raw:: latex

   \setcounter{hppgline}{0}

.. _description-1:

Description
~~~~~~~~~~~

This program calculates :math:`{\rm atan2}(\frac{y}{x})`. Result is in
the range :math:`-180` to :math:`+180`.

.. _usage-1:

Usage
^^^^^

``GTO Z001 x R/S y R/S``

.. _program-listing-1:

Program Listing
~~~~~~~~~~~~~~~

R1.25cm L2.5cm L10.0cm

| & ``LBL Z`` &Start of program.
| & ``STO X`` &Store :math:`x` in ``X``.
| & ``STOP`` &Wait for user R/S.
| & ``STO Y`` &Store :math:`y` in ``Y``.
| & ``RCL Y`` &Recall ``Y``. Note: this is also the entry point for
  subroutine.
| & ``RCL X`` &Recall ``X``.
| & ``\div`` &Take ratio of rise over run (:math:`\frac{y}{x}`).
| & ``ATAN`` &Calculate :math:`\arctan(\frac{y}{x})`.
| & ``STO R`` &Save as an interim result in ``R``.
| & ``RCL X`` &Test sign of ``X``.
| & ``x > 0?`` &Is :math:`x` positive?
| & ``GTO Z027`` &If so then go to end of program.
| & ``RCL Y`` &Recall ``Y`` ...
| & ``SGN`` &Calculate its sign ...
| & ``45`` &
| & ``\times`` &then multiply it by 45.
| & ``RCL X`` &Get ``X`` value.
| & ``x = 0?`` &Is it equal to zero?
| & ``RTN`` &If so then return the value of the stack (:math:`\pm`\ 45)
| & ``180`` &Setup offset depending on sign of :math:`y`.
| & ``STO -R`` &Initially subtract 180— we do this at a minimum.
| & ``RCL Y`` &Get ``Y`` value.
| & ``x < 0?`` &Is it negative?
| & ``GTO Z027`` &If yes, then we are done since we already subtracted
  180.
| & ``360`` &If :math:`y` is positive then we have to add 360...
| & ``STO +R`` &... for a total addition of 180.
| & ``RCL R`` &Get the angle.
| & ``RTN`` &Return to calling function.

.. _example-1:

Example
~~~~~~~

In the following example we calculate
:math:`{\rm atan2}(\frac{+1.5}{-1.0})` using the following steps:
``GTO Z001`` ``0.00000`` ``1.5`` ``1.5`` ``R/S`` ``1.50000`` ``-1.0``
``-1.0`` ``R/S`` ``-33.69007``

.. _comments-1:

Comments
~~~~~~~~

Users have to be careful about a couple of things:

#. Angles are calculated in *degrees. Confirm calculator setting before
   using this function.*

#. User is responsible for ensuring that :math:`x` and :math:`y` are
   **never both zero.**

avswr
-----

.. raw:: latex

   \setcounter{hppgline}{0}

.. _description-2:

Description
~~~~~~~~~~~

This program calculates actual VSWR given measured VSWR and cable loss
to antenna.

.. _usage-2:

Usage
^^^^^

``GTO V001 M R/S L R/S``

.. _program-listing-2:

Program Listing
~~~~~~~~~~~~~~~

R1.25cm L2.5cm L10.0cm

| & ``LBL V`` &Start of program.
| & ``STO M`` &Save measured VSWR in ``M``.
| & ``STOP`` &Pause for entry of cable loss (in dB)
| & ``+/-`` &Negate cable loss …
| & ``10`` &…and convert to ratio
| & ``\div`` &
| & ``10^{x}`` &
| & ``STO L`` &Save as cable loss
| & ``RCL M`` &Get measured VSWR and calculate reflected power ratio
| & ``1`` &
| & ``-`` &
| & ``RCL M`` &
| & ``1`` &
| & ``+`` &
| & ``\div`` &
| & ``x^{2}`` &
| & ``STO R`` &Save reflected power ratio
| & ``RCL L`` &Calculate actual VSWR at antenna
| & ``\sqrt{x}`` &
| & ``RCL R`` &
| & ``RCL L`` &
| & ``\div`` &
| & ``\sqrt{x}`` &
| & ``+`` &
| & ``RCL L`` &
| & ``\sqrt{x}`` &
| & ``RCL R`` &
| & ``RCL L`` &
| & ``\div`` &
| & ``\sqrt{x}`` &
| & ``-`` &
| & ``\div`` &
| & ``RTN`` &Return to calling function.

.. _example-2:

Example
~~~~~~~

Calculate the actual VSWR of an antenna where the measured VSWR is
1:1.13 and cable loss is 4.7dB: ``GTO V001`` ``0.00000`` ``1.13`` ````
``R/S`` ``1.13000`` ``4.7`` ```` ``R/S`` ``1.4394``

How this program works
~~~~~~~~~~~~~~~~~~~~~~

:math:`VSWR` is the ratio of the sum and difference of forward and
reflected voltages:

.. math:: VSWR = {{V_f+V_r}\over{V_f-V_r}}

Since power is proportional to the square of the voltage, (1) can be
expressed in terms of power

.. math:: VSWR = {{\sqrt{P_f}+\sqrt{P_r}}\over{\sqrt{P_f}-\sqrt{P_r}}}

By setting :math:`P_f` equal to :math:`1` and rearranging (2) we can
solve for :math:`P_r`

.. math:: P_r = \left({{VSWR-1}\over{VSWR+1}}\right)^{2}

Cable loss is normally expressed in decibels but for our purposes we can
simply express it as a factor of less than 1 where :math:`P_a` is power
at the antenna and :math:`P_t` is power from the transmitter.

.. math:: L = {{P_a }\over{ P_t}}

Taking into account the cable loss and measured forward and reverse
power we can calculate VSWR at the antenna

.. math:: VSWR = {{\sqrt{P_f \times L}+\sqrt{P_r \div L}}\over{\sqrt{P_f \times L}-\sqrt{P_r \div L}}}

Again we set :math:`P_f` to :math:`1` so a simplied version of (5)
becomes the actual VSWR at the antenna

.. math:: VSWR = {{\sqrt{L}+\sqrt{P_r \div L}}\over{\sqrt{L}-\sqrt{P_r \div L}}}

HP12c
=====

canfin
------

.. raw:: latex

   \setcounter{hppgline}{0}

.. _description-3:

Description
~~~~~~~~~~~

This package provides four different functions: - calculate best average
consecutive earnings given the final salary and the average percentage
increase over n years - calculate the real rate of return based on
investment return and a given rate of inflation - calculate the
effective interest rate for a Canadian mortage where compounding occurs
at a different interval than the mortgage payments - calculate the
compound percentage increase or decrease of value over time in years

.. _usage-3:

Usage
^^^^^

Best average earnings: enter final salary in ``FV``, annual percentage
increase expresses as a multipler (e.g. 2 percent is entered as 1.02)
and averaging period in ``n``. ````

.. _program-listing-3:

Program Listing
~~~~~~~~~~~~~~~

| R2.0cm R3.0cm L5.0cm ``RCL i`` & ``,4512`` &Best average consecutive
  earnings launch point
| ``RCL n`` & ``,4511`` &
| ``1`` & ``,`` &
| ``-`` & ``,30`` &
| ``y^x`` & ``,21`` &
| ``1`` & ``,`` &
| ``RCL i`` & ``,4512`` &
| ``-`` & ``,30`` &
| ``\times`` & ``,20`` &
| ``RCL n`` & ``,4511`` &
| ``\times`` & ``,20`` &
| ``1`` & ``,`` &
| ``RCL i`` & ``,4512`` &
| ``RCL n`` & ``,4511`` &
| ``y^x`` & ``,21`` &
| ``-`` & ``,30`` &
| ``\div`` & ``,10`` &
| ``1/x`` & ``,22`` &
| ``RCL FV`` & ``,4515`` &
| ``\times`` & ``,20`` &
| ``R/S`` & ``,31`` &
| ``GTO 001`` & ``,43,33,001`` &jump to a whole bunch more text …
| ``1`` & ``,`` &
| ``0`` & ``,`` &
| ``0`` & ``,`` &
| ``\div`` & ``,10`` &
| ``1`` & ``,`` &
| ``+`` & ``,40`` &
| ``1/x`` & ``,22`` &
| ``x \gtrless y`` & ``,34`` &
| ``1`` & ``,`` &
| ``0`` & ``,`` &
| ``0`` & ``,`` &
| ``\div`` & ``,10`` &
| ``1`` & ``,`` &
| ``+`` & ``,40`` &
| ``\times`` & ``,20`` &
| ``1`` & ``,`` &
| ``-`` & ``,30`` &
| ``1`` & ``,`` &
| ``0`` & ``,`` &
| ``0`` & ``,`` &
| ``\times`` & ``,20`` &
| ``R/S`` & ``,31`` &
| ``GTO 023`` & ``,43,33,023`` &
| ``1/x`` & ``,22`` &
| ``x \gtrless y`` & ``,34`` &
| ``2`` & ``,`` &
| ``0`` & ``,`` &
| ``0`` & ``,`` &
| ``\div`` & ``,10`` &
| ``1`` & ``,`` &
| ``+`` & ``,40`` &
| ``x \gtrless y`` & ``,34`` &
| ``y^x`` & ``,21`` &
| ``1`` & ``,`` &
| ``-`` & ``,30`` &
| ``1`` & ``,`` &
| ``0`` & ``,`` &
| ``0`` & ``,`` &
| ``\times`` & ``,20`` &
| ``R/S`` & ``,31`` &
| ``GTO 046`` & ``,43,33,046`` &
| ``RCL FV`` & ``,4515`` &
| ``RCL PV`` & ``,4513`` &
| ``\div`` & ``,10`` &
| ``RCL n`` & ``,4511`` &
| ``1/x`` & ``,22`` &
| ``y^x`` & ``,21`` &
| ``1`` & ``,`` &
| ``-`` & ``,30`` &
| ``1`` & ``,`` &
| ``0`` & ``,`` &
| ``0`` & ``,`` &
| ``\times`` & ``,20`` &
| ``R/S`` & ``,31`` &
| ``GTO 064`` & ``,43,33,064`` &
| ``ENTER`` & ``,36`` &
| ``RCL n`` & ``,4511`` &
| ``1`` & ``,`` &
| ``+`` & ``,40`` &
| ``y^x`` & ``,21`` &
| ``CHS`` & ``,16`` &
| ``1`` & ``,`` &
| ``+`` & ``,40`` &
| ``x \gtrless y`` & ``,34`` &
| ``CHS`` & ``,16`` &test comment
| ``1`` & ``,`` &
| ``+`` & ``,40`` &
| ``n`` & ``,11`` &
| ``R/S`` & ``,31`` &
| ``GTO 078`` & ``,43,33,078`` &
| ``STO 0`` & ``,440`` &storing into register 0
| ``-`` & ``,30`` &
| ``ENTER`` & ``,36`` &
| ``\times`` & ``,20`` &
| ``RCL 0`` & ``,450`` &
| ``\div`` & ``,10`` &
| ``+`` & ``,40`` &
| ``R/S`` & ``,31`` &
| ``GTO 093`` & ``,43,33,093`` &

.. _example-3:

Example
~~~~~~~

In the following example we calculate
:math:`{\rm atan2}(\frac{+1.5}{-1.0})` using the following steps:
``GTO Z001`` ``0.00000`` ``1.5`` ``1.5`` ``R/S`` ``1.50000`` ``-1.0``
``-1.0`` ``R/S`` ``-33.69007``

.. _comments-2:

Comments
~~~~~~~~

Users have to be careful about a couple of things:

#. Angles are calculated in *degrees. Confirm calculator setting before
   using this function.*

#. User is responsible for ensuring that :math:`x` and :math:`y` are
   **never both zero.**
