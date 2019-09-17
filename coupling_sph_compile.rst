.. _section-coupling-compile:

Compile the code for tracking
#############################

For the coupling case, you will need to generate two makefiles: (1) without coupling (Grid A) and (2) with coupling (Grid B). See an example of a complete "Makefile" :ref:`here <subsection-compile>`.

**GRID A**

MAKEFILE

 .. code-block:: rest

   #---------BEGIN MAKEFILE-----------
        ...
        ...
        EXEC   = funwave_nocoupling      # for example

   #-----------------------------------
   #    PRECISION ...
   #
   #-----------------------------------
   ## FLAGS
   ## Flag numbers are arbitrary, but necessary 

        FLAG_1 = -DDOUBLE_PRECISION
   #     FLAG_# = -DCARTESIAN           # using spherical coordinates; CARTESIAN is commented out

   #  if parallel add
        FLAG_2 = -DPARALLEL
   #  if intel compiler add
        FLAG_6 = -DINTEL
        
        ...

   #----------------------------------
   # mpi defs
   #----------------------------------
   ## COMPILER INFO

        ...

        FC = mpif90     # for example

 The compiled executable file is "funwave_nocoupling.exe".

**GRID B**

MAKEFILE

 .. code-block:: rest

   #---------BEGIN MAKEFILE-----------
        ...
        ...
        EXEC   = funwave_coupling      # for example

   #-----------------------------------
   #    PRECISION ...
   #
   #-----------------------------------
   ## FLAGS
   ## Flag numbers are arbitrary, but necessary 

        FLAG_1 = -DDOUBLE_PRECISION
   #     FLAG_# = -DCARTESIAN           # using spherical coordinates; CARTESIAN remains commented out
        FLAG_7 = -DCOUPLING             # add DCOUPLING to GRID B (receiving grid)

   #  if parallel add
        FLAG_2 = -DPARALLEL
   #  if intel compiler add
        FLAG_6 = -DINTEL
        
        ...

   #----------------------------------
   # mpi defs
   #----------------------------------
   ## COMPILER INFO

        ...

        FC = mpif90     # for example

 The compiled executable file is "funwave_coupling.exe".
