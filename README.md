# home-assistant-shutter-control

Shutter control 

A script file to control my home shutters.

Script file is composed of 3 parts:

1. Partially close, modo siesta :)

Shutters are partially close in phases allowing to pass a minimum amount of light trought the holes that link the blind slat.

2. Close all shutters.

To close all the shutters in phases

3. Open all shutters

To open all the shutters in phases



Remarks about timeout.

The wait_template in Home Assistant is designed to pause script execution until a specific condition is met (for example, a shutter is closed or in a certain position) or until the specified timeout is reached.

Avoid unnecessary waiting: If the timeout is too long for a fast moving shutter (such as the one in the South Hall), the script will wait for the maximum time set, even if the shutter has already finished its movement. This unnecessarily slows down the overall sequence.

Detect problems early: If the timeout is too short for a shutter that takes longer, the wait_template will timeout before the shutter finishes, continue_on_timeout: false, the script will stop, which is good for detecting a problem, but means that the blind did not complete its action within the expected time. Setting timeout correctly ensures that the script only stops if there is a real problem (i.e.: such as a stuck shutter) and not because of a wrong configured timeout.

Accurate timing: For a phased sequence, it is crucial that each phase is completed before the next phase begins. A well adjusted timeout ensures that the script waits just the right amount of time for each group of blinds.
