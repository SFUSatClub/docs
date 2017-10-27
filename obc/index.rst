OBC Subsystem
========================

Serial Interface
~~~~~~~~~~~~~~~~~~~~
Baud: 115200

Line ending: CRLF

Recommended serial terminal: `miniterm.py`_

The OBC does not echo back characters as you type, but it will send back the
full command it received once you hit enter (i.e., when the OBC encounters a
CRLF EOL sequence).

Current command format follows the structure of::

  <command> <subcommand> [<args>...]


Overview
........
Here are the useful commands that are currently implemented::

  get tasks
  get runtime
  get heap
  get minheap
  task suspend <id>
  task resume <id>

get
  Get various metrics from the OBC.

  tasks
	Show state, priority, and free stack of running tasks.
	Note that the Num column is not the task id used for other commands.
	See the ``TASK_IDS`` enum in sfu_cmds.h_ for task ids.
	::
	  Task            State   Prio    Stack   Num
	  serial          R       3       38      7
	  IDLE            R       0       103     5
	  state           B       3       260     10
	  tickle          B       4       95      9k
	  main            B       2       52      1
	  FreqPST         B       1       54      2
	  radio           B       5       77      8
	  InfreqPST       B       1       45      3
	  Receiver        B       2       49      4
	  blinky          S       1       99      6
  
  runtime
	Show task CPU utilization statistics.
	::
	  Task            Abs             Perc
	  serial          13409184                1%
	  IDLE            954919186               95%
	  tickle          57110           <1%
	  main            3053180         <1%
	  FreqPST         51296           <1%
	  state           14571           <1%
	  InfreqPST       12141           <1%
	  Receiver        510286          <1%
	  radio           30604595                3%
	  blinky          54453           <1%

  heap
	Show amount of heap currently available.
	::
	  4440 bytes

  minheap
	Show lowest amount of heap ever reached.
	::
	  3352 bytes

task
  Run various task-related commands.

  suspend <id>
	Suspend the task with id <id>

	For example, from ``TASK_IDS``, we see that ``TASK_RADIO`` has an ID of ``1``.
	Thus, the following command will suspend the radio task.
	::
	  task suspend 1
	  
  resume <id>
	Resume the task with id <id>

	The following command will resume the radio task, ``TASK_RADIO``.
	::
	  task resume 1


Check the ``CMD_TABLE`` macro in `sfucmds.h`_ for the list of registered commands.
Commands are implemented in `sfucmds.c`_. 

Command ``sched`` is implemented but not tested, reason being the current
parsing for this command expects to recieve the raw byte representation of the
command to schedule. This is assisted by parsing the argument as hexadecimal
characters, but of course is still not feasible to input manually. Won't matter
too much since there are easier ways to test the scheduling system, such as:

- Hardcode a variety of ``sched`` struct and populate it with simple fields
  retrieved from serial commands, then fire these off into the scheduling system.

- Test scheduling system using the radio.


.. _sfucmds.h: https://github.com/SFUSatClub/obc-firmware/blob/master/SFUsat/sfu_cmds.h#L41
.. _sfucmds.c: https://github.com/SFUSatClub/obc-firmware/blob/master/SFUsat/sfu_cmds.c
.. _miniterm.py: https://github.com/pyserial/pyserial/blob/master/serial/tools/miniterm.py

Radio SPI Interface
~~~~~~~~~~~~~~~~~~~~

TODO
