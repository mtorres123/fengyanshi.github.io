.. _section-meteo-compile:

Compile the code for meteotsunami case
######################################

**Makefile**

See an example of a complete "Makefile" :ref:`here <subsection-compile>`.

For this example, you will need to update the :code:`EXEC` variable, and make sure the appropriate :code:`FLAGS` are active in the "Makefile":

.. code-block:: rest

   #---------BEGIN MAKEFILE-----------
        ...
        ...
        EXEC   = funwave_meteo      # for example

   #-----------------------------------
   #    PRECISION ...
   #
   #-----------------------------------
   ## FLAGS
   ## Flag numbers are arbitrary, but necessary 

        FLAG_1 = -DDOUBLE_PRECISION
        FLAG_4 = -DCARTESIAN 
        FLAG_12 = -DMETEO
   
   # if parallel add
        FLAG_2 = -DPARALLEL

   # if intel compiler add
        FLAG_6 = -DINTEL
        ...

   #----------------------------------
   # mpi defs
   #----------------------------------
   ## COMPILER INFO

        ...

        FC = mpif90     # for example

The compiled exe file is "funwave_meteo.exe".
