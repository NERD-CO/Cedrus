## Using Cedrus
* ```Cedrus_TTL.m``` is a function that enables hexidecimal TTL to NLX transmission during a behavioral task.
* This function is based off of the script ```CedrusSetup.m```. The script provides more detail about the code written in the function. 
* The source of ```CedrusSetup.m```, ```getByte.m```, and ```setPulseDuration.m``` can be found in support documents on the [Cedrus website](https://www.cedrus.com/support/xid/matlab.htm).

### Requirements
* ```getByte.m``` and ```setPulseDuration.m``` must be on the path for ```Cedrus_TTL.m``` to work

### User guide
#### 1. Assign distinct TTL markers for event types
#### 
* An example of what this would look like can be found in ```hexidecmial TTL key.txt```.
#### 2. Every time you wish to send a TTL, the following code should be written immediately following the line containing the event.
* *Example:*
  ```   
        subjdata.ts.stimStart(t) = Screen('Flip',wind,[],1); %show the stimuli
        if do_TTL
            %DatapixxAOttl(); % TTL pulse marking screen flip that shows choice options
            write(device,sprintf("mh%c%c",70, 0), "char"); % TTL pulse marking screen flip that shows choice options
        end
##### Where ```DatapixxAOttl();```, used to send TTLs with Datapixx, is replaced by ```write(device,sprintf("mh%c%c",70, 0), "char");```
#### 3. Call ```Cedrus_TTL.m``` with outputs from within the main behavioral task function or script
##### 
* *Example:* ```[ports, device] = Cedrus_TTL()```
