Applications
############

Crytsalline systems
====================


Anharmonic energy
----------------------

**Conventional:**

.. math::
   U^{\rm ah} = \left< U \right> - \frac{d(N-1)}{2} k_{\rm B} T - U^{\rm lat} 

**Mapped averaging:**

.. math::
   U^{\rm ah} =  \left< U + \frac{1}{2} {\bf F}\cdot\Delta{\bf r}\right> - U^{\rm lat} 

|

Anharmonic pressure
----------------------

**Conventional:**

.. math::
   P^{\rm ah} = \left< P^{\rm vir} \right> + \rho k_{\rm B}T - P^{\rm qh} - P^{\rm lat} 

**Mapped averaging:**

.. math::
   P^{\rm ah} = \left< P^{\rm vir} + c \; {\bf F}\cdot\Delta{\bf r} \right>  - P^{\rm lat} 

where :math:`c` is a constant and given by, :math:`c = \frac{\beta P^{\rm qh} - \rho}{d\left(N-1\right)}`


Equivalence of both formulations:
----------------------------------

The equivalence between both conventional and mapped-averaging expressions can be easily seen by recognizing this equality for crystalline systems:

.. math::
   \left<{\bf F}\cdot\Delta{\bf r} \right> = - d\left(N-1\right) k_{\rm B} T 
Plugging this expression into the HMA expressions yields the conventional average expression.


**Proof:**

The general expression for the configurational partition function is given by:

.. math::
   Q = \int e^{-\beta U} {\rm d} {\bf x} 

For crtsralline systems, we use :math:`\Delta {\bf x} \equiv {\bf x} - {\bf x}^{\rm lat}`

.. math::
   Q = \int_{\rm WS} e^{-\beta U} \, {\rm d}^{dN}\Delta x 
Where the integration is carried out withing the Wigner-Seitz (WS) volume of each atom. This can be written as

.. math::
   Q = \int_{\rm WS} {\rm d}^{dN-1}\Delta x \; \int_{\rm WS}  e^{-\beta U} \, {\rm d} \Delta x_1
Using integration by parts:

.. math::
   Q = \int_{\rm WS}  \; \left[\Delta x_1 e^{-\beta U}\right]_{\Delta x_1^{\rm min}}^{\Delta x_1^{\rm max}} {\rm d}^{dN-1}\Delta x
   \;\; -\beta \int_{\rm WS}  F_1 \Delta x_1 \; e^{-\beta U} {\rm d}^{dN}\Delta x
The surface (first) term on the right-hand side vanishes due to large values of :math:`U` at the surface of the WS volume. Dividing by Q, we finally get:

.. math::
   \left<F_1 \Delta x_1 \right> = - k_{\rm B} T 

For :math:`d(N-1)` degrees-of-freedom, we get: :math:`\left<{\bf F}\cdot\Delta{\bf r} \right> = - d\left(N-1\right) k_{\rm B} T`


Liquid system
==============

A
---

B
---