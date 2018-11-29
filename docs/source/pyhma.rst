pyhma
######

``pyhma`` is an implementation of the `mapped-averaging <https://pubs.acs.org/doi/abs/10.1021/acs.jctc.6b00018>`_ method for crystalline systems, where the harmonic behavior is used to define the mapping "velocity"; hence the name harmonically-mapped averaging (hma). The ensemble averages are obtained in ``pyhma`` via post-processing of outputs from molecular simulation codes (currently, VASP) in two steps:

**1. Reading raw data**
   Raw data (lattice vectors, configurations, forces, energies, and pressures) are extracted from molecular simulation code output and written to the following .dat files:

   * **lattice.dat [Å]:** contains lattice vectors and coordinates of the initial (minimized) system.
   * **posfor.dat [Å and eV/Å]:** contains the atomic positions and forces at each simulation step.
   * **u.dat [eV]:** contains the potential energy at each step.
   * **p.dat [GPa]:** contains the virial pressure (:math:`-dU/dV`, with uniform scaling of coordinates) at each step.

For the case of VASP, this step is done using the :class:`pyhma.ReadVASP` class to read the OUTCAR files as following:

.. code-block:: python

  >>> import pyhma
  >>> r = pyhma.ReadVASP('OUTCAR1','OUTCAR2')
  >>> r.read()

Or, it can be invoked using the ``pyhma`` script:

.. code-block:: bash

   pyhma --readvasp OUTCAR1 OUTCAR2

.. warning::

   The configuration of the first molecular simulation step must be one at minimized energy (i.e., zero force on each).

**2. Computing averages**

In this step, the .dat files generated in the first step are used to compute (conventional and hma) anharmonic ensemble averages (currently, energy and pressure) using the :class:`pyhma.Simulation` class. Since the .dat files are universal, this step is independent on the molecular simulation code.

Here is an example of hpw to use 

.. code-block:: python

   >>> import pyhma
   >>> sim = Simulation()
   >>> sim.run()  # computes conventional and hma estimates for each configuration
   >>> data = sim.get_statistics() # computes average, stochastic uncertainty (1:math:`\sigma`), and correlation
   >>> print(' Anharmonic energy (conv.)  :', data['uahc'], '[eV/atom]')
   >>> print(' Anharmonic energy (hma)    :', data['uahm'], '[eV/atom]')
   >>> print(' Anharmonic pressure (conv.):', data['pahc'], '[GPa]')
   >>> print(' Anharmonic pressure (hma)  :', data['pahm'], '[GPa]')

    Anharmonic energy (conv.)  : {'avg': -2.8459263453288584, 'err': 0.001774507316355033, 'corr': -0.07466066266723995} [eV/atom]
    Anharmonic energy (hma)    : {'avg': -2.8477249829084768, 'err': 0.0002183231516704866, 'corr': -0.31459267645202793} [eV/atom]
    Anharmonic pressure (conv.): {'avg': 1.1533150204254468, 'err': 0.04680482720426752, 'corr': -0.046065939075653525} [GPa]
    Anharmonic pressure (hma)  : {'avg': 1.1155015968330577, 'err': 0.01369902534482252, 'corr': 0.0741058952868103} [GPa]



.. code-block:: bash

   pyhma --compute

**UNITS**

.. autoclass:: pyhma.ReadVASP
   :members:

.. autoclass:: pyhma.Simulation
   :members:


|

|

|

|

|

|

|

|

|