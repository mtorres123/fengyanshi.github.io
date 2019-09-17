.. _section-coupling-gridb:

GRID B (solitary wave case)
###########################

.. figure:: images/simple_cases/solitary_nesting.jpg
    :width: 400px
    :align: center
    :height: 350px
    :alt: alternate text
    :figclass: align-center

.. NOTE:: Step 3: Run funwave_coupling

**Setup in "input.txt"**

Use the GRID A "input.txt" (:ref:`section-coupling-grida`) as the foundation of the "input.txt" file for GRID B. Make the following changes / updates to the GRID B "input.txt":

 Send the results to a folder named "output_2":

 .. code-block:: rest

        !-----PRINT-----
         RESULT_FOLDER = output_2/

 
 Update the dimensions of the domain to 2000 x 3 (x and y directions, respectively):

 .. code-block:: rest
        
        !-----DIMENSION-----
        
         Mglob = 2000   ! x-dir
         Nglob = 3      ! y-dir
 
 Update the grid spacing in spherical coordinates:

 .. code-block:: rest

        !-----GRID-----
         Lon_West = 120.0
         Lat_South = 0.0
         Dphi = 0.000017986
         Dtheta = 0.00005

 Remove the wavemaker:

 .. code-block:: rest

        !-----WAVEMAKER-----
         WAVEMAKER = nothing

 Add the coupling file you made in Step 2:

 .. code-block:: rest

        !-----COUPLING-----
         COUPLING_FILE = ../make_nest_file/coupling.txt         # set relative path to coupling.txt

**Postprocessing**

An example postprocessing MATLAB script is located in :code:`/benchmarks/sph_nesting/postprocessing`.
