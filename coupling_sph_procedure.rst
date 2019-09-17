.. _section-coupling-procedure:

Coupling procedure
******************

In this coupling case, there are two grids in the spherical system: (1) the coarse grid (low resolution, GRID A) and (2) the fine grid (higher resolution, GRID B). GRID B is nested in GRID A at i = 500 (point). A solitary wave is specified in GRID A as the initial condition.

To complete this example, follow the steps below:

1. Run GRID A using :code:`funwave_nocoupling` compiled *without* :code:`-DCOUPLING` (see :ref:`section-coupling-compile`). Specify a station file "station.txt" for output at the coupling boundaries. Follow :ref:`section-coupling-grida`. 
2. Make a coupling file "coupling.txt" using the output from GRID A (see :ref:`section-coupling-file`).
3. Run GRID B using :code:`funwave_coupling` compiled *with* :code:`-DCOUPLING` (see :ref:`section-coupling-compile`). Specify the coupling file "coupling.txt" in "input.txt". Follow :ref:`section-coupling-gridb`.
