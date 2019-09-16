.. _section-tracking-basics:

Basics for model setup
######################

In the directory :code:`/simple_cases/rip_tracking/work/`, you will find multiple instances of the input files that are specific to different variations of this example, e.g., regular ("input.txt") versus solitary ("input\_solitary.txt") wavemaker configurations. It should be noted that the model will accept only the file named "input.txt". Therefore, if you want to switch wavemaker cases, you will need to modify the primary "input.txt" file.

**Computational domain**

.. figure:: images/simple_cases/bathy_tracer.png
    :width: 400px
    :align: center
    :height: 320px
    :alt: alternate text
    :figclass: align-center
   
The bathymetry file for this example is "depth_a15.txt" located in :code:`/simple_cases/rip_tracking/bathy/`. If the "depth_a15.txt" file is not present, you will need to run the :code:`makebathy.m` MATLAB script to generate the file.

**Setup in "input.txt"**

The initial setup of "input.txt" for this example is the same the :ref:`section-rip-sediment` example with the addition of Lagrangian tracers. Description of the "input.txt" file for a regular monochromatic wave with normal incidence can be found :ref:`here <section-rip-sediment-basics>`. 

You will need to modify or add the following sections to "input.txt":

 Update the title to reflect a new simulation:

 .. code-block:: rest

        !-----TITLE-----
         TITLE = 2D_beach_rip_sediment_tracer

 Update the computational time to 500.0 s:

 .. code-block:: rest

        !-----TIME-----
         TOTAL_TIME = 500.0

 Add the Lagrangian tracking feature just before the :code:`OUTPUT` section:

 .. code-block:: rest

        !-----TRACKING-----
         TRACER_FILE = tracers.txt

 The "tracers.txt" file is located in the working directory: :code:`/simple_cases/rip_tracking/work/`. Refer to :ref:`section-tracer-setup` for more information on the Lagrangian tracer feature.

Refer to :ref:`section-rip-sediment-reg` for setup of the :code:`SEDIMENT` section, and :ref:`definition_sediment` for parameter definitions.

**Postprocessing**

For postprocessing examples, MATLAB and Python scripts are located in :code:`/simple_cases/rip_tracking/postprocessing/`.
