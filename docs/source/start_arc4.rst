Getting started on ARC4
=======================

All Postgraduate researchers are entitled to an account on ARC4. You can request an account IT, as detailed on the `ARC4 docs page <https://arcdocs.leeds.ac.uk/getting_started/request_hpc_acct.html>`_. Taught students may also be entitled but must speak to their supervisor before submitting a request. 

Once logged on, you can set up the correct module environment using 

.. code-block:: console
		
	$ module use /nobackup/CESM/module_env
	$ module load cesm 

By default, this will load cesm2.1.3, but you can specify a version using ``cesm/<version>``. Each time you log off ARC4 the environment is reset, so you will need to start each new session by setting the environment. Loading the ``cesm`` module also loads the `Earth System Modeling Framework <https://earthsystemmodeling.org/>`_ (ESMF) module, a high-perfomance, flexible software infrastructure for building and coupling Earth system models. Both modules are found within the ``module_env`` directory.  


Batch Jobs
----------

ARC4 uses a batch scheduler called Sun Grid Engine (SGE), which allocates resources and prioritises jobs that are submitted to the compute nodes through the queue. There is a fair share policy in place, so a users' priority will decrease with the more resources they use. More information on writing job submission scripts (job scripts) can be found here: `ARC4 job scripts <https://arcdocs.leeds.ac.uk/usage/batchjob.html#job-scripts>`_.
