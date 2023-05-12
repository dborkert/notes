## *05/05/2023*
### Tasks
- [X] Create Task List
- [X] check emails
- [X] Open teams
- [X] fix helix saved jobs freezing
- [ ] Solder LED for /SWRFAULT2 on CL0056
### Notes
Arrival time: 9:15

The problem with the helix was a stack overflow. The arrays for the flash job server were going way out of bounds.
This was causing configuration data and other important things to be overwritten. The Machine() instantiation was being
called from an interrupt context. This causes the RTOS to trigger a hardfault.

A second bug found on the helix was the firmware would allow a user to save while the USB job was being transfered to the printer.
This would cause the job to never find the end and then trigger a hardfault. I fixed this by both canceling the job load when there is
an error, and not allowing saving during a USB job.

Talked with allen about the rotary for the galvo machine and how the microstepping algorithm in the stepper controller seems to be struggling
around the zero current crossing. Potiential fixes are a larger inducance motor or a higher frequency.

## *05/08/2023*
### Tasks
- [X] Create Task List
- [X] check emails
- [X] Open teams
- [X] Test USB print speed
- [X] Fix Update issue over USB
- [X] Solder LED for /SWRFAULT2 on CL0056
- [ ] Regression test the center-center for helix
- [ ] Final code cleanup and notes for helix
### Notes
Arrival time: 9:20AM
Leave Time: 5:45PM

Today, I spent the day working on the helix. I fixed an issue where the machine wouldn't update over USB. Turns out the first buffer fill was
getting immediately cleared in the USBJobServer. I then fixed an issue where the jobRunner thread was hanging because of a mutex that was never
getting released when the machine was recovering commands (via a big job). My limit logic to prevent the carriage from slamming into the right
side of the machine is faulty in center-center mode. the Carriage then gets a left offset and engraves in the completly the wrong spot. I would
like to have a right side limit, but the old board doesn't so don't I need to determine whether it is necessary.

I soldered and LED to the /SWRFault2 pin on the CL0056 R05 board that was in a 100W laser when a RF MOSFET blew up.

These are the settings of the different machines as of 05082023.

Mini 18 Settings:
- X Home: -265
- y Home: -20
- X R Home : -2400
- Y R Home : +650
- Focus Adj: -20
- Laser Match: -01
- Stamp Match: 00
- Bed Size: 18 x 12
- AirA Raster: Yes
- AirA Vector: Yes
- Autodelete: No
- Sys Unit: Inch
- Laser TM: 03
- Laser TI: 03
- M. Control X: No
- M. Control Y: No
- Load FL Job: Yes
- Europe: No
<br>

Helix Settings:
- X Home: -155
- y Home: -10
- X R Home : -2400
- Y R Home : +650
- Focus Adj: -03
- Laser Match: -01
- Stamp Match: 00
- Bed Size: 24 x 18
- AirA Raster: Yes
- AirA Vector: Yes
- Autodelete: No
- Sys Unit: Inch
- Laser TM: 03
- Laser TI: 03
- M. Control X: No
- M. Control Y: No
- Load FL Job: Yes
- Europe: No

## *05/09/2023*
### Tasks
- [X] Create Task List
- [X] Check emails
- [X] Open teams
- [X] Figure Out Center-Center Limits
- [ ] Remove option to revert firmware if no previous firmware exists
- [ ] Code Cleanup
- [ ] Run Final tests on Helix
- [ ] Get started on fixing raster drift due to vector match
### Notes
Arrival time: 8:30PM
Departure time: 6:00PM

I spent all day trying to figure out how to prevent the carriage from crashing into the side in center-center mode. However, it is very difficult because the axis gets reset every time the "home position" changes. I gave up for now and just removed all logic that prevents the carriage from running into the side. This is the same behaviour that the old board shows. The motor drives have protection and the position controller quickly faults, so it's not dangerous to the electronics, but not great. That is literally all I worked on today and got nowhere UGH.
## *05/10/2023*
### Tasks
- [X] Create Task List
- [X] check emails
- [X] Open teams
- [X] Figure Out Center-Center Limits
- [X] Code Cleanup
- [ ] Run Final tests on Helix
- [X] Get started on fixing raster drift due to vector match
### Notes
Arrival time: 9:20
Departure Time: 5:30

I spent more of the day fixing the problems with the carriage hitting the edge of the machine for the mini helix. In the end, I removed all of my new logic and just stuck with what was there previously. I also cleaned up some of the fpga logic. I felt quite awful all day, brain fog and just felt almost like I had a slight hangover. I think it was due to the intense exercise I did on tuesday.

## *05/11/2023*
### Tasks
- [X] Create Task List
- [X] check emails
- [X] Open teams
- [X] Fix raster drift due to vector match
### Notes
Arrival time: 9:00
Departure time: 3:45

When the vector match is enabled for raster, it doesn't seem to affect laser match. I am not quite sure how that works, but pretty extensive testing showed this to be the case. It may be because the add and subtration of extra points is symmetrical. Anyway, I put up a pull request where I simply remove the logic that disabled the vector match when in raster mode. The power went out, so I ended up going home early.


## *05/12/2023*
### Tasks
- [X] Create Task List
- [X] check emails
- [X] Open teams
- [ ] Merge in Vector Match Fix ESD-1701 (not yet wait for 1082)
- [ ] Start on no engrave power with unidirectional on ESD-1650
- [ ] Test Mini 24 in Technical Support
- [ ] Begin Specification document Library
### Notes
Arrival time: 9:25
Departure Time:

- merge in ESD-1701
    - this is postponed due to use being too close to the release of 1.0.8.1 to get added into that release
    therefore Allen requested changes so it'll be added in 1.0.8.2.

## *05/15/2023*
### Tasks
- [ ] Create Task List
- [ ] check emails
- [ ] Open teams
### Notes
Arrival time:

## *05/16/2023*
### Tasks
- [ ] Create Task List
- [ ] check emails
- [ ] Open teams
### Notes
Arrival time:

## *05/17/2023*
### Tasks
- [ ] Create Task List
- [ ] check emails
- [ ] Open teams
### Notes
Arrival time:

## *05/18/2023*
### Tasks
- [ ] Create Task List
- [ ] check emails
- [ ] Open teams
### Notes
Arrival time:

## *05/19/2023*
### Tasks
- [ ] Create Task List
- [ ] check emails
- [ ] Open teams
### Notes
Arrival time:
