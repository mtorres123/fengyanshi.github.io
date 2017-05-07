30 deg irregular waves and an obstacle
################################################

.. figure:: images/simple_cases/eta_inlet_shoal_irr_30deg_obs.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

* Add wavemaker

 WAVEMAKER = WK_IRR

 DEP_WK = 10.0

 Xc_WK = 250.0

 Yc_WK = 0.0

 Ywidth_WK = 20000.0

 FreqPeak = 0.0893

 FreqMin = 0.03

 FreqMax = 0.3

 Hmo = 1.00

 GammaTMA = 3.3

 ThetaPeak = 30.0

 Sigma_Theta = 10.0

* Add periodic boundary condition

 PERIODIC = T

* Add OBSTACLE FILE

 OBSTACLE_FILE = obs_shoal_inlet.txt
