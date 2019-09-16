.. _section-meteo-flat:

Meteotsunami: Gausian pressure and flat bottom  
##############################################

In this example, you will add a pressure source with an elliptical shape Guassian distribution. Review :ref:`section_meteo_module` for a description of the pressure source. In addition, refer to :ref:`definition_meteo` for parameter definitions. The primary "input.txt" and corresponding "meteo_data.txt" files are located in :code:`/simple_cases/meteo_tsunami`.

**Model setup**

.. figure:: images/simple_cases/meteo_layout.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

**Setup in "input.txt"**

Model configuration: Model dimensions: 100 km x 600 km. Water depth is 40 m in the whole domain. Pressure source is an elliptical shape Gaussian distribution described in the section of METEO-MODULE in
`INTRODUCTION <theory_formulation.html>`_. The moving speed of the source is specified as 20 m/s which is close to the critical speed to make Proudman Resonance. 

 Set a descriptive title for your simulation:

 .. code-block:: rest
        
        !-----TITLE-----
         TITLE = meteo_tsunami


 If running in parallel, set the number of processers in X and Y:
 
 .. code-block:: rest

        !-----PARALLEL INFO-----
         PX = 4 
         PY = 1

 Set the bathymetry to the following:
 
 .. code-block:: rest

        !-----DEPTH-----
         DEPTH_TYPE = FLAT
         DEPTH_FLAT = 40.0

 (refer to :ref:`definition_grid` for parameter descriptions)

 Send the results to a folder named "output":

 .. code-block:: rest

        !-----PRINT-----
         RESULT_FOLDER = output/

 Set the dimensions of the domain to 600 km x 100 km (x and y directions, respectively):

 .. code-block:: rest

        !-----DIMENSION-----
         Mglob = 600   ! x-dir
         Nglob = 100   ! y-dir

 Set the total computational time, plot time, and screen intervals to 30000.0 s, 360.0 s, and 50000.0 s, respectively. If printing results to a station file, use 360.0 s:

 .. code-block:: rest
        
        !-----TIME-----
         TOTAL_TIME = 30000.0
         PLOT_INTV = 360.0
         SCREEN_INTV = 360.0
         PLOT_INTV_STATION = 50000.0

 Set the grid spacing in x and y to 500.0 m:

 .. code-block:: rest

        !-----GRID-----
         DX = 500.0
         DY = 500.0

 Set the sponge layer width to 7.5 m and 5.0 m on the west and east boundary, respectively:

 .. code-block:: rest

        !-----SPONGE LAYER-----
         DIFFUSION_SPONGE = F
         FRICTION_SPONGE = F
         DIRECT_SPONGE = F
         Csp = 0.10
         CDsponge = 1.0
         Sponge_west_width = 7.5
         Sponge_east_width = 5.0
         Sponge_south_width = 0.0
         Sponge_north_width = 0.0
         R_sponge = 0.85
         A_sponge = 5.0
         
 A periodic boundary condition is not applied in this example.

 **Keep the default values** for the :code:`FRICTION, NUMERICS`, and :code:`WET-DRY` sections of "input.txt". Refer to :ref:`section-definitions` for a description of all parameters.

 Set the following output files to TRUE:

 .. code-block:: rest

        !-----OUTPUT-----
         DEPTH_OUT = T
         ETA = T
         Hmax = T
         Hmin = T
         OUT_METEO = T    ! T will have output of pressure distribution

 Add the meteo tsunami pressure source to the bottom of "input.txt":

 .. code-block:: rest

        !-----METEO TSUNAMI-----
         MeteoGausian = T
         METEO_GAUSIAN_FILE = meteo_data.txt    ! this file can be found in the meteo_tsunami/ folder
   
 The pressure source is specified in the "meteo_data.txt" file in the current directory. 

  .. code-block:: rest
  
        Meteo data file
        NJ
        time, x, y, dP(mb), SigmaX, SigmaY, Angle(0 = +x direction)
        0.0       0.0 25000.0   5.0 10000.0 100000.0 0.0
        36000.0  720000.0 25000.0  5.0 10000.0 10000.0 0.0     

**Postprocessing**

For a postprocessing example, MATLAB script :code:`plot_wave.m` is located in :code:`/simple_cases/meteo_tsunami`. The figure below shows the Proudman Resonance produced by the moving pressure source:

.. figure:: images/simple_cases/resonance.jpg
    :width: 300px
    :align: center
    :height: 600px
    :alt: alternate text
    :figclass: align-center


