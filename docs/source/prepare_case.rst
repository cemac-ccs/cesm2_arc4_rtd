Preparing a case
================

Change directory to your ``cesm_prep`` directory and use the ``create_newcase`` script, located in the central installation to create your case,

.. code-block:: console
		
		$ cd $HOME/cesm_prep
		$ $CESM_HOME/cime/scripts/create_newcase --case $HOME/cesm_prep/<case_name> --compset <compset> --res <grid_resolution>

Change working directory into the case directory

.. code-block:: console
		
		$ cd $HOME/cesm_prep/case_name

Run setup and build

.. code-block:: console
		
		$ ./case.setup
		$ ./case.build

After running ``./case.setup``, you can use ``./preview_run`` to see the information that will be used at run time. This includes the number of nodes requested, the commands for setting the environment and the run commands. It is useful to check the run command is submitting your job to the correct queue, with the correct resources, and whether archiving is set up correctly.

Input data
----------

The model is configured to look for the input data in a central directory ``/nobackup/CESM/inputdata`` so that all users can share downloaded files. This is currently read only to all users except CEMAC staff. If you find your case is missing files, please contact CEMAC (cemac-support@leeds.ac.uk) and include the compset and resolution configuration that you want.

Archiving
---------

The CIME framework allows for short-term and long-term archiving of model output. This is particularly useful when the model is configured to output to a small storage space and large files may need to be moved during larger simulations. On ARC4, the model is configured to use short-term archiving, but not yet configured for long-term archiving. Short-term archiving is on by default for compsets and can be toggled on and off using the ``DOUT_S`` parameter set to True or False (see :doc:`making_changes`). When ``DOUT_S=TRUE``, calling ``./case.submit`` will automatically submit a "st_archive" job to the batch system that will be held in the queue until the main job is complete. This can be configured in the same way as the main job for a different queue, wallclock time, etc, however the default should be appropriate in most cases. Note that the main job and the archiving job share some parameter names so a flag (``--subgroup``) specifying which you want to change, if not both, should be used. The archive is currently set up to move .nc files and logs from ``/nobackup/<username>/case_sims/<case_root>`` to ``/nobackup/<username>/case_sims/archive``. As such, the quota being used is the communal ``/nobackup`` space whether archiving is switched on or off. There is a lot of storage available in this space, however it is not backed up and should only be left there for short periods as it will be removed after 90 days. If a user wants to archive their files directly to a different location, this can be set using the ``DOUT_S_ROOT`` parameter.
