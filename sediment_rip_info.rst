.. _section-rip-sediment-basics:

Basics for model setup
######################

In the directory :code:`/simple_cases/sediment_rip/work/`, you will find the primary "input.txt" file for this example. External files to define the bathymetry of the domain are located in :code:`/simple_cases/sediment_rip/bathy/`.

The baseline case for a rip current can be found :ref:`here <example_rip_current>`.

**Computational domain**

.. figure:: images/simple_cases/depth_2rip.jpg
    :width: 300px
    :align: center
    :height: 350px
    :alt: alternate text
    :figclass: align-center

**Setup in "input.txt"**

See an example of a complete "input.txt" :ref:`here <section-definitions>`.

For this example, you will set the following in "input.txt". **Remember that all parameters are case sensitive**.

 Set a descriptive title for your simulation:

 .. code-block:: rest

        !-----TITLE-----
         TITLE = 2D_beach_rip_sediment

 If running in parallel, set the number of processors in X and Y:

 .. code-block:: rest

        !-----PARALLEL INFO-----
         PX = 4
         PY = 4

 Set the bathymetry by using the provided depth file:

 .. code-block:: rest

        !-----DEPTH-----
         DEPTH_TYPE = DATA
         DEPTH_FILE = ../bathy/depth_a15.txt

 If the :code:`depth_a15.txt` file is not present in the :code:`/bathy/` directory, you will need to generate the file using the provided :code:`makebath.m` script.

 Send the results to a folder named "output":

 .. code-block:: rest

        !-----PRINT-----
         RESULT_FOLDER = output/
  
 Set the dimensions of the domain to 312 m X 100 m in x and y, respectively. *Note: we only read 100 rows from the depth file shown in the figure*.

 .. code-block:: rest

        !-----DIMENSION-----
         Mglob = 312    ! x-dir
         Nglob = 100    ! y-dir

 (refer to :ref:`definition_grid` for parameter definitions)

 Set the total computational time, plot time, station printing interval, and screen interval to 1000.0 s, 100.0, 0.5 s, and 100.0 s, respectively.

 .. code-block:: rest

        !-----TIME-----
         TOTAL_TIME = 1000.0
         PLOT_INTV = 100.0
         PLOT_INTV_STATION = 0.5
         SCREEN_INTV = 100.0

 Set the grid spacing in x and y to 1.0 m and 2.0 m, respectively:

 .. code-block:: rest

        !-----GRID-----
         DX = 1.0 m
         DY = 2.0 m

 Add a wavemaker for a monochromatic wave with normal incidence:

 .. code-block:: rest

        !-----WAVEMAKER-----
         WAVEMAKER = WK_REG
         DEP_WK = 8.0
         Xc_WK = 280.0
         Yc_WK = 0.0
         Tperiod = 8.0
         AMP_WK = 0.5
         Theta_WK = 0.0
         Delta_WK = 3.0
         
 (refer to :ref:`definition_wavemaker` for parameter definitions)

 Set the periodic boundary conditions to TRUE:

 .. code-block:: rest

        !-----PERIODIC BOUNDARY CONDITION-----
         PERIODIC = T

 Set the sponge layer width to 60.0 m on the east boundary:

 .. code-block:: rest

        !-----SPONGE LAYER-----
         DIFFUSION_SPONGE = F
         FRICTION_SPONGE = T
         DIRECT_SPONGE = T
         Csp = 0.0
         CDsponge = 1.0
         Sponge_west_width = 0.0
         Sponge_east_width = 60.0
         Sponge_south_width = 0.0
         Sponge_north_width = 0.0

 **Keep the default values** for the :code:`PHYSICS, NUMERICS`, and :code:`WET-DRY` sections. Refer to :ref:`section-definitions` for a description of all parameters.

 Set the viscosity breaking scheme to FALSE. The breaking terms will be ignored. Refer to :ref:`example_breaking` for an example of the wave breaking schemes.

 .. code-block:: rest

        !-----BREAKING-----
         VISCOSITY_BREAKING = F

 Set the wave average parameters to the following:

 .. code-block:: rest

        !-----WAVE AVERAGE-----
         T_INTV_mean = 50.0
         STEADY_TIME = 100.0

 Set the following output files to TRUE:

 .. code-block:: rest

        !-----OUTPUT-----
         DEPTH_OUT = T
         ETA = T
         U = T
         V = T
         Umean = T
         Vmean = T
         ETAmean = T
         MASK = T
         WaveHeight = T
      
 The addition of the sediment parameters is described on page :ref:`section-rip-sediment-reg`.

**Postprocessing**

 For postprocessing examples, MATLAB and Python scripts are located in :code:`/simple_cases/sediment_rip/postprocessing/`.
