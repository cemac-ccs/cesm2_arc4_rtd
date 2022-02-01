Making changes to a case
===================================

At this point, you can make any changes to your case setup, such as changing the wallclock time, number of cores etc. ARC4 has a maximum job time limit of 24 hours and has 40 cores per node. 

You can query settings using the function

.. code-block:: console
		
		$ ./xmlquery <name_of_setting>

Adding ``-p`` as a flag allows you to look up partial names, e.g.

.. code-block:: console
		
		$ ./xmlquery -p JOB

		Output:
		Results in group case.run
		        JOB_QUEUE: 40core-192G.q
                        JOB_WALLCLOCK_TIME: 01:30:00

		Results in group case.st_archive
                        JOB_QUEUE: 40core-192G.q
                        JOB_WALLCLOCK_TIME: 0:20:00

When you know which setting you want to change, you can do so using 

.. code-block:: console
		
		$ ./xmlchange <name_of_setting>=<new_value>

For example to change the wallclock time to 30 minutes, without knowing the exact name, you could do

.. code-block:: console
		
		$ ./xmlquery -p WALLCLOCK

		Output:
		Results in group case.run
                        JOB_WALLCLOCK_TIME: 01:30:00

		Results in group case.st_archive
                        JOB_WALLCLOCK_TIME: 0:20:00
		
.. code-block:: console
		
		$ ./xmlchange JOB_WALLCLOCK_TIME=00:30:00 --subgroup case.run

.. note::
   
   The flag ``--subgroup case.run`` is used to change only the main job wallclock without affecting the st_archive wallclock. 
