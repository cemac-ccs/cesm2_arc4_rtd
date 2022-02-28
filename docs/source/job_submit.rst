Submitting a job
================

To use ARC4 compute nodes, you can submit a job to the queue through a batch scheduler. It requires you to request the number of cores (or nodes), memory and time needed and pointing to the program you wish to run. The batch scheduler takes your resources into account and allocates your job a place in the queue. More information on writing job submission scripts (job scripts) can be found here: `ARC4 job scripts <https://arcdocs.leeds.ac.uk/usage/batchjob.html#job-scripts>`_.

For CESM2, the CIME framework has been configured for ARC4 so that you can use the package functions to submit jobs. Before you do so, you can preview commands that will be run at submission time using 

.. code-block:: console
		
		$ ./preview_run

You can submit the job using 

.. code-block:: console
		
		$ ./case.submit

The default queue is 40core-192G, which has 5960 cores available for use (ARC4 has 40 cores per node). There are other queues available, though most are privately owned. If you have access to another queue that you would like to use, you can choose it when preparing your case using ``./xmlchange``, e.g.

.. code-block:: console
		
		$ ./xmlchange JOB_QUEUE=<name_of_queue>

.. note::

   This will change the JOB_QUEUE for the short term archive job as well (st_archive). If you only want to change the queue of your main job, you can add the --subgroup case.run flag as in :doc:`making_changes`.




The case can then be run on that queue using the submit command, as before

.. code-block:: console
		
		$ ./case.submit
