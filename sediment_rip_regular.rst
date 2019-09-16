.. _section-rip-sediment-reg:

Regular waves with normal incidence
###################################

.. figure:: images/simple_cases/eta_c_dep_5.jpg
    :width: 500px
    :align: center
    :height: 250px
    :alt: alternate text
    :figclass: align-center

Figure: (left) snapshot of surface elevation (5th output), (middle) sediemnt concentration and current field, (right) bathymetry change (5th output) 

Recall that the baseline case for a rip current can be found on page :ref:`example_rip_current`.

Here, we will add the :code:`SEDIMENT` properties to the "input.txt" file from :ref:`section-rip-sediment-basics`. 

 Set the following sediment parameters:
 
 .. code-block:: rest

        !-----SEDIMENT-----
         Bed_Change = T
         BedLoad = T
         D50 = 0.0005
         Sdensity = 2.68
         n_porosity = 0.47
         WS = 0.0125
         Shields_cr = 0.055
         Shields_cr_bedload = 0.047
         Tan_phi = 0.7
         Kappa1 = 0.3333
         Kappa2 = 1.0
         MinDepthPickup = 0.1 

 (refer to :ref:`definition_sediment` for parameter definitions)

