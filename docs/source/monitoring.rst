Monitoring jobs
===================================

You can check the status of all your jobs using the command 
.. code-block:: console
		$ qstat -u $USER

Also, if you want to check the demand on the queues you can use

.. code-block:: console
		$ qstat -g c 

to see a table of node availability. 

Jobs can be cancelled using 
.. code-block:: console
		$ qdel <job_id>

For further information on the ARC4 docs, see `Monitoring jobs on ARC4 <https://arcdocs.leeds.ac.uk/usage/batchjob.html#monitoring-jobs>`_

