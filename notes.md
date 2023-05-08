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
 - [ ] Create Task List
 - [ ] check emails
 - [ ] Open teams
 - [ ] Solder LED for /SWRFAULT2 on CL0056
 - [ ] Regression test the center-center for helix
 - [ ] Final code cleanup and notes for helix
 ### Notes
 Arrival time: 9:20AM
 
 
  ## *05/09/2023*
 ### Tasks
 - [ ] Create Task List
 - [ ] check emails
 - [ ] Open teams
 ### Notes
 Arrival time:
 
  ## *05/10/2023*
 ### Tasks
 - [ ] Create Task List
 - [ ] check emails
 - [ ] Open teams
 ### Notes
 Arrival time:
 
  ## *05/11/2023*
 ### Tasks
 - [ ] Create Task List
 - [ ] check emails
 - [ ] Open teams
 ### Notes
 Arrival time:
 
  ## *05/12/2023*
 ### Tasks
 - [ ] Create Task List
 - [ ] check emails
 - [ ] Open teams
 ### Notes
 Arrival time:
 
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
