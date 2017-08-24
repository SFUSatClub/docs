High Level Design Requirements
===================================
These represent estimated requirements for the team to discuss, elaborate on, and push back on.

Informed by :ref:`con-ops`
Satellite Requirements
Mission life: 1 year
Bus size 1U
Bus weight 1 kg
Orbit: LEO, any inclination (ISS)
Individual subsystem failure should not affect any other subsystem in the short term(power distribution and structure notwithstanding)
No liquids, gasses, pressure vessels, thrusters, fire
All subsystems must have serial communication interfaces and controllable by the OBC
Position knowledge: < 300km
Single ON switch
Comms
Downlink and uplink combined 120 kbytes per day
Frequency must be ITU amateur satellite sanctioned
Power2
Attitude Determination & Control
Determination accuracy of <10 degrees in three axis
de-spin and stabilization for post deployment spins of up to 30deg/s
Continuous single face pointing capability of nadir +/- 10 degrees except for the axis in the direction of said face
State switching
Able to enable Low Power for each subsystem
Able to turn each sub system off and on
Command and Control
Execute commands immediately or time delayed up to 7 days into future
Able to validate command receipt and execution
Non-volatile storage: ability to store health monitoring data, config files, job queue, s/c states for 7 days. 
Thermal
Passive thermal control for PCBs
Battery: Active thermal control
Health Monitoring
Subsystem level thermal shutdown
Subsystem level latchup detection and reset
Temperature and current monitoring at subsystem level
Subsystem level recovery routines for SEL, SEU, infinite loops
Structural
No moving parts (with the exception of deployable antenna)
Launch survivability, should not liquify on launch
Cubesat launcher standards 
Total Mass loss from outgassing less than 1%
Payload
Peak power 2W
5% duty cycle 
1U, 1kg
Fixed attitude requirements (no major attitude correction in orbit)
7 month unpowered room temp storage 
Payload should include its own processing and data storage
