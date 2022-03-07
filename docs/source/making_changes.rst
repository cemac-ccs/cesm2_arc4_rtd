Making changes to a case
========================

After creating a new case, the CIME functions can be used to make changes to the case setup, such as changing the wallclock time, number of cores etc. ARC4 has a maximum job time limit of 24 hours and has 40 cores per node. 

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
		
		$ ./xmlchange JOB_WALLCLOCK_TIME=00:30:00 --subgroup case.run

		$ ./xmlquery JOB_WALLCLOCK_TIME

		Output:
		Results in group case.run
		        JOB_WALLCLOCK_TIME: 00:30:00

		Results in group case.st_archive
                        JOB_WALLCLOCK_TIME: 0:20:00

			
.. note::
   
   The flag ``--subgroup case.run`` is used to change only the main job wallclock without affecting the st_archive wallclock.


.. note::

   If you try to set a parameter equal to a value that is not known to the program, it might suggest using a ``--force`` flag. This may be useful, for example, in the case of using a queue that has not been configured yet, but use with care!


Some changes to the case must be done before calling ``./case.setup`` or ``./case.build``, otherwise the case will need to be reset or cleaned, using ``./case.setup --reset`` and ``./case.build --clean-all``. These are as follows.

* Before calling ``./case.setup``, changes to ``NTASKS``, ``NTHRDS``, ``ROOTPE``, ``PSTRID`` and ``NINST`` must be made, as well as any changes to the ``env_mach_specific.xml`` file, which contains some configuration for the module environment and environment variables. 
   
* Before calling ``./case.build``, ``./case.setup`` must have been called and any changes to ``env_build.xml`` and ``Macros.make`` must have been made. This includes whether you have edited the file directly, or used ``./xmlchange`` to alter the variables.

Many of the namelist variables can be changed just before calling ``./case.submit``.
