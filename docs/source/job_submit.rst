Submitting a job
================

To use ARC4 compute nodes, you can submit a job to the queue through a batch scheduler. It requires you to request the number of cores (or nodes), memory and time needed and pointing to the program you wish to run. The batch scheduler takes your resources into account and allocates your job a place in the queue. More information on writing job submission scripts (job scripts) can be found here: `ARC4 job scripts <https://arcdocs.leeds.ac.uk/usage/batchjob.html#job-scripts>`_.

For CESM2, the CIME framework has been configured for ARC4 so that you can use the package functions to submit jobs. Before you do so, you can preview commands that will be run at submission time using 

.. code-block:: console
		
		$ ./preview_run

You can submit the job using 

.. code-block:: console
		
		$ ./case.submit

The default queue is 40core-192G, which has 5960 cores available for use (ARC4 has 40 cores per node). There are other queues available, though most are privately owned. If you have access to another queue through a specific project, you can choose it when preparing your case using ``./xmlchange``. On ARC4, usually the project would be specified and it would automatically sort your submitted job to the correct queue assigned to that project. The way CESM2 is set up, if only the project is specified, it will default to the main queue causing your job to hang. Both the project and the associated queue must be specified, e.g.

.. code-block:: console
		
		$ ./xmlchange PROJECT=<name_of_project>
		$ ./xmlchange JOB_QUEUE=<name_of_queue>

.. note::

   This will change the PROJECT and JOB_QUEUE for the short-term archive job as well (st_archive). If you only want to change the queue of your main job, you can add the ``--subgroup case.run`` flag as in :doc:`making_changes`.

.. note::

   If you try to set a queue name that is not known, you will need to use the ``--force`` flag.

You can check the qsub command again using ``./preview_run`` and the case can then be run using the submit command, as before with ``$ ./case.submit``.
