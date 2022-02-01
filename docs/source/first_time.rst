First time usage
===================================

Set up the correct module environment using 

.. code-block:: console
		
	$ module use /nobackup/CESM/module_env
	$ module load cesm 

By default, this will load cesm2.1.3, but you can specify a version using ``cesm/<version>''.
Make a directory in your $HOME directory to store case setups. 

.. code-block:: console
	$ mkdir $HOME/cesm_prep

Scripts from the central installation (/nobackup/CESM/cesm2.1.3) are copied here for use with a specific case, e.g. case.setup and env_run.xml. Your run submission outputs, run.*.o* and run.*.e*, will also be created and updated here. 

Data output and detailed log files are written to a directory in ``/nobackup''. If you do not already have a user directory there, you need to make one using

.. code-block:: console
	$ mkdir /nobackup/<username>

and replace ``<username>'' with an appropriate name. 

It is important to note that any files written to your /nobackup directory will **not** be backed up, as the name implies. This is a temporary storage place and any output that you wish to keep must be moved to appropriate storage, else it will be deleted after 90 days without access. Your $HOME directory is backed up once a week, however it is limited to 10GB per user. 
