.. _con-ops:

Concept of Operations
========================


Payload Objective
=========================
CHIME requires characterizing the complex gains of the telescope. Characterization in the longitudinal direction is performed with natural astronomical sources sweeping east to west of the sky. It is however difficult to kind a similar source to characterize the complex gain along the latitudinal axis. An orbiting artificial source with knowledge of signal characteristic moving with a longitudinal component relative to the telescope can provide the additional information needed to fully characterize CHIME’s performance. Signal characteristics is the time dependent power received at the telescope with an accuracy of 1:10^4 relative to the telescope’s antenna beam.

TODO: make success matrix


Operating Parameters
========================
CHIME requires <1 degree phase uncertainty which requires 1.08 deg euler angle uncertainty of spacecraft position from the perspective of CHIME. Assuming a worst cast of 400km circular sun-synchronous orbit (assume 7.5km/s orbital velocity). A small angle approximation at the height in the horizon per second: atan(7.5km/400km) = 1 deg/s. Minimum sample rate is 1 Hz. This can be increased to increase accuracy. This data will need to be time stamped to a greater accuracy.

CHIME can only store data for a few seconds, therefore the ground reference station must be on site at DRAO.

Due to the CHIME and ground reference power measurement methods being different, SI calibrated measurements must be performed.
Precision requirement ???????
Accuracy must be below 1:10^4 (-4db?)

A rough link analysis was performed using AMSAT-IARU_Link_Model_Rev2.5.5.xls by Jan King. Sheet in the spreadsheet is denoted by (“sheet name”). Because this is for CHIME, only downlink signal chain is considered. LEO with 800 km apogee and perigee with slant angle of 0 degrees resulting in a slant range of 3293.2 km. (Orbit, Atmos. & Ionos. Losses) Frequency of 790MHz is selected to show worst case free space path losses. (Frequency) Cubesat and ground station radio losses and noise figures are set at their default values and ground station LNA gain=18db.(Transmitter, Receiver) The ground station uses the default yagi antenna while the spacecraft uses the default dipole. (Antenna Gain) Antenna polarization is left at default values. (Antenna Polarization) Non-coherent FSK with a data rate of 10bps was chosen for the ease of implementation. (Modulation-Demodulation Method, Downlink Budget)
45 degrees to horizontal
Condition
Min TX Pr
attitude

The reference ground station will be at DRAO. It will be a 2 DOF active Yagi (>14dBi) with 2 polarizations each with its own front-end acquisition.

The payload will consist of a radio transmitter with one or more carriers in the 400 MHz to 800 MHz band. The carriers will be modulated with a predefined binary sequence with a bounded small cross-correlation within a set that will be used by CHIME to isolate the payload signal from other sources. The transmitter will require a reliable controller to enable transmissions dependent on current location above standard earth coordinates to comply with international telecommunications regulations. The transmitter will operate continuously while within line of sight of the telescope and fall silent when not. The payload will require a capability to record and transmit time dependent position and attitude data to be used by the ground segment. This spatial data can either be time-series data taken throughout the fly-by or a single point used as an initial condition in a orbital and attitude propagation model. The ground segment will take this data and compute the time dependent power density received at the telescope which will then be handed off to CHIME researchers for use in calibrating their telescope.

External Stakeholders
==========================

Current deliberation to determine mission requirements is being done in collaboration with Gilbert Hsyu MSc and Dr,. Seth Siegel both members of McGill Cosmology Instrumentation Laboratory. Gilbert Hsyu has been primarily working on calibrating CHIME. We have also been in talks with Dr. Keith Vanderlinde, U of T Dept. of Astronomy and Astrophysics. CHIME is a collaboration between UBC, U of T, McGill, and Dominion Radio Astrophysical Observatory. Dr. Rodney Vaughan of SFU Engineering Science is advising on instrumentation and antenna development for the payload.
Responsibilities for Work
At this point in time it is not known how much of the payload design, construction and testing will be done by McGill Cosmology or other CHIME members. With high confidence the antenna for the payload will be produced internally with assistance from Dr. Rodney Vaughan. As required by the CSDC all integration activities will be performed internally. Internal work will be done by the CHIME payload sub-team and RF sub-team when designs or skills overlap.
Development, Integration, Operation
Payload development will follow standard subsystem timelines. Highly integrated RF chips can be used to minimize design workload for all parties in order to meet an early prototype deadline of Summer 2017. The payload will require extensive testing and characterization of power performance, antenna response, etc. Testing and characterization will occur in partnership with SFU’s Sierra Wireless Mobile Communications Laboratory starting in Summer 2017 and extending to a few months before launch.

Integration work may be shared with the RF Comms subsystem due to shared resources on the spacecraft, although this has yet to be determined. Nonetheless, because the payload will follow a similar schedule with all other subsystems there exists no scheduling conflicts. The payload will require performance characterization post-integration due to the high precision needed. Post-integration characterization can however be pushed to a date after the CSDC if demanded by the schedule.

Once in orbit, the payload will require further characterization from the ground before it can be used by CHIME. The extent of on-orbit characterization required is yet unknown. Once characterize we can move into the CHIME calibration campaign; the length of which is yet unknown. Ground operations will need to determine the time-series power density at the Dominion Observatory for the duration of the CHIME calibration campaign. The ground power density with the binary sequence will be sent to the appropriate authority of the CHIME team.  CHIME characterization will be revisited until CHIME or the spacecraft’s end-of-life.

Adherence to CSDC, CubeSat and other constraints
====================================================
The activities required leading up to payload integration with spacecraft are is achievable within the time frame given by the CSDC. In order to have a latitudinal component to the spacecraft as it flies over the telescope, the orbital inclination must be above that of the latitude of the Dominion Radio Observatory (49.3°). Section 3.2 of CSDC General Rules & Requirements recommends a sun-synchronous(98°) or ISS(51°) orbiting mission. The requirement CSDC-0020 and the payload requires post-launch spacecraft orbit determination capabilities with an accuracy that will be determined at a later date. The payload contains only electronics and antenna structure and other materials that are non-volatile and stable for storage(CSDC-0030, CSDC-0050). The mission can operate for several year or months under agreement with Industry Canada and FCC as described in the section Development, Integration, Operation(CSDC-0040, CSDC-0080, CSDC-0160, CSDC-0220, CSDC-0230, CDS-3.4.1, CDS-3.4.2). Attitude determination must be fault tolerant for successful mission operation in the event of a failure(CSDC-0170). Electronics are all common COTS components(CSDC-0190). The payload may have antenna deploying from CubeSat(CDS-3.1.2, CDS-3.2.4, CDS-3.4.4). Power needs are comparable to the telemetry radio; requires no significantly large power storage (CDS-3.1.6). COTS component outgassing will need to be determined(CDS-3.1.8)
Data Delivery
Mission Data

Housekeeping
================
In accordance with CSDC-0120, we shall record 4 points of telemetry at least once every 5 minutes. Larry has said that data points for 4 batteries = 1 telemetry item. 

Collection frequencies will default to 5 minutes if appropriate, but can be changed from the ground. Additionally, other telemetry points can be added to this list, and it may be different depending on system state. For example, in safe mode, it would be wise to transmit antenna deployment state.

Todo: Define telemetry list for different mission states. Ex: for startup/safe mode, transmit antenna deployment status. Low power, pretty much just do battery and overall system health 

Telemetry List:
Battery SOC (per cell)
OBC temperature
OBC current consumption
Battery temperature (per cell?)
Solar cell voltage (per panel)
RF power amplifier temperature (for both ICs)
RF subsystem current consumption
Orientation ← too high level?
Voltage of 5V rail
Mission epoch (at time of telemetry send, plus all data is time tagged)	
Error queue - RTC status, any overflows or otherwise unusual error messages
Spacecraft state
“Command Handbook”

Tasking, Scheduling and Control
====================================
Synchronization of clock between ground and spacecraft: satellite mission epoch will be sent out at the time of each telemetry packet transmission. Additionally, current mission epoch can be requested at any time. Mission epoch is accurate to the second.

Scheduling: commands can be scheduled for an arbitrary time in the future, or to be run immediately. The system will save the command queue to triple redundant flash and to internal EEPROM at each change, so it can be recovered in the event of a power loss. 

States:

From Computing subsystem’s “State Machine”

Major Operating modes: 

Safe Mode
In this mode, the system will be transmitting the safe telemetry set 

Communication Architecture
How ground station and spacecraft interact.

What is the sampling frequency of the ground station power meters?
What is the hardware link to CHIME?

Mission Timeline
======================
4 switches: 
Pull before flight
3 switches that engage on deployment
Debug Mode
Assembled and tested. All functions work as verified through testing.
Pre-launch
Deployment switch prevents battery charging and discharge. Batteries of fully charged. “Pull before flight” pin is removed it closes its parts of the battery charging and discharging. (All deployment pins are ANDed).
Launch
Deployment from P-pod. Deployment switch enables battery charging and power distribution to all subsystems. All 3 deployment switches ingage to fully engage battery charging and discharge. The spacecraft is now in the “primed” state. OBC begin countdown for antenna deployment. Once antenna is deployed (30 min later), enter “safe” state where the spacecraft transmits spacecraft status beacon every 10 seconds. Command from ground transitions spacecraft from safe state to ready state.
Commissioning
Ready state task scheduling will be used.
Verification of attitude determination.
CHIME transmission verification.
Power cycle characterization (charging and usage)
RF link characterization (see test section in CDR)
Extra
Verify NORAD TLE with radio ranging
Propagate from initial deployment vector (does launch provider give use deployment state vector?)

Nominal Operation 
CHIME calibration pass is scheduled few orbits before scheduled pass (~ 1 week).
Telemetry
Health monitoring
CHIME
3D magnetic sensor
Sleep
Tracking
Decommissioning (end of life)
Deorbiting
Power off
Radio off
Tracking



