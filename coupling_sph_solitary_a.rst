.. _section-coupling-grida:

GRID A (solitary wave case)
###########################

.. figure:: images/simple_cases/solitary_nesting.jpg
    :width: 400px
    :align: center
    :height: 350px
    :alt: alternate text
    :figclass: align-center

.. NOTE:: Step 1: Run funwave_nocoupling

**Setup in "input.txt"**

For this example, you will set the following in "input.txt". **Remember that all parameters are case sensitive**.

 If running in parallel, set the number of processors in X and Y:

 .. code-block:: rest

        !-----PARALLEL INFO-----
         PX = 2
         PY = 2 

 Set the bathymetry to match the figure above:

 .. code-block:: rest

        !-----DEPTH-----
         DEPTH_TYPE = FLAT
         DEPTH_FLAT = 8.0

 (refer to :ref:`definition_grid` for parameter descriptions)

 Send the results to a folder named "output_1":

 .. code-block:: rest

        !-----PRINT-----
         RESULT_FOLDER = output_1/
  
 Set the dimensions of the domain to 1500 x 3 (x and y directions, respectively):

 .. code-block:: rest
        
        !-----DIMENSION-----
        
         Mglob = 1500   ! x-dir
         Nglob = 3      ! y-dir

 Set the total computational time, plot time, station printing interval, and screen interval to 400.0 s, 1.0 s, 0.0 s, and 1.0 s, respectively:

 .. code-block:: rest

        !-----TIME-----
         TOTAL_TIME = 400.0
         PLOT_INTV = 1.0
         PLOT_INTV_STATION = 0.0
         SCREEN_INTV = 1.0

 Set the grid spacing in spherical coordinates:

 .. code-block:: rest

        !-----GRID-----
         Lon_West = 120.0
         Lat_South = 0.0
         Dphi = 0.000035972
         Dtheta = 0.0001
  
 Add a wavemaker for a solitary wave:

 .. code-block:: rest

        !-----WAVEMAKER-----
         WAVEMAKER = INI_SOL
         AMP = 0.1
         DEP = 10.0
         LAGTIME = 0.0
         XWAVEMAKER = 1000.0

 Refer to :ref:`definition_wavemaker` for parameter definitions.
         
 Set the periodic boundary condition to FALSE:

 .. code-block:: rest

        !-----PERIODIC BOUNDARY CONDITION-----
         PERIODIC = F

 (refer to :ref:`info_periodic` for an example)

 Set the sponge layer width to 180.0 m on the left boundary:

 .. code-block:: rest

        !-----SPONGE LAYER-----
         DIFFUSION_SPONGE = F
         FRICTION_SPONGE = T
         DIRECT_SPONGE = T
         Csp = 0.0
         CDsponge = 1.0
         Sponge_west_width = 180.0      ! this line
         Sponge_east_width = 0.0
         Sponge_south_width = 0.0
         Sponge_north_width = 0.0

 (refer to :ref:`info_sponge` for example of 2D sponge case)

 **Keep the default values** for the :code:`PHYSICS, NUMERICS, WET-DRY,` and :code:`BREAKING` sections. Refer to :ref:`section-definitions` for a description of all parameters. See :ref:`example_breaking` for more an example of wave breaking.

 Set the wave average properties:

 .. code-block:: rest

        !-----WAVE AVERAGE-----
         T_INTV_mean = 240.0
         STEADY_TIME = 480.0

 Set the number of stations to 3 and include the station file. Set the following output files to TRUE:

 .. code-block:: rest

        !-----OUTPUT-----
         NumberStations = 3
         STATIONS_FILE = station.txt

         DEPTH_OUT = T
         ETA = T
         U = T
         V = T
         
 (refer to :ref:`definition_output` for parameter definitions)

