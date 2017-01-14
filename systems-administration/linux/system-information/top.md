top
===

Shows all running processes

#### Load Average

load average .00 .01 .05:
	
	cpu usage in 1 minute is 0%
	cpu usage at 5 minutes is 10%
	cpu usage at 10 minuts is 50%


#### Nice Values 

(invoke kernel use at certain priority levels)

	-20   # highest priority
	19    # lowest priority

#### Usage

	shift m        # orders by memory usage
	shift p        # orders by cpu usage
	r[PID] -20     # renice PID to the highest priority
	k[PID]         # kill the process in top, 15: kill when finished, 9: kill process and force quit
