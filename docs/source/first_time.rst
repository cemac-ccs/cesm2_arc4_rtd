First time usage
===================================

The home directory for CESM2 code is located at ``/nobackup/CESM`` on ARC4, where you can find the ported versions (currently 2.1.3), module environments and input data directories. The ported versions are configured to run on ARC4, with the correct batch and compiler information, and these are the versions available for use. You do not need to download your own copy of the model code unless you want to use a different version, or make changes to the code. There are a few things you need to do to prepare your account for using these versions.

To use the case scripts, such as create_newcase, you will need to be added to the UNIX group arc-cesm2, which will give you the correct group permissions. Please :ref:`contact CEMAC<contact>`.

Make a directory in your $HOME directory to store case setups. 

.. code-block:: console
		
	$ mkdir $HOME/cesm_prep

Scripts from the central installation (/nobackup/CESM/cesm2.1.3) are copied here for use with a specific case, e.g. case.setup and env_run.xml. Your run submission outputs, run.*.o* and run.*.e*, will also be created and updated here. 

Data output and detailed log files are written to a directory in ``/nobackup``. If you do not already have a user directory there, you need to make one using

.. code-block:: console
		
	$ mkdir /nobackup/<username>

and replace <username> with an appropriate name. 

It is important to note that any files written to your /nobackup directory will **not** be backed up, as the name implies. This is a temporary storage place and any output that you wish to keep must be moved to appropriate storage, else it will be deleted after 90 days without access. Your $HOME directory is backed up once a week, however it is limited to 10GB per user. 
