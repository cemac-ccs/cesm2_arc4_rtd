Preparing a case
===================================

Every time you log off ARC4, the module environment is reset, so you will need to begin each session with

.. code-block:: console
	$ module use /nobackup/CESM/module_env
	$ module load cesm

Change directory to your ``cesm_prep'' directory and use the ``create_newcase'' script, located in the central installation to create your case,

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

Next, the input data files may need to be downloaded. The model is configured to look for the input data in a central directory ``/nobackup/CESM/inputdata'' so that all users can share downloaded files. This is currently read only to all users except CEMAC staff. Please contact CEMAC (cemac@leeds.ac.uk) if you need to download input data, and include the compset and resolution configuration that you want. 
