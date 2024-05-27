# Case Study

##MOCA Based Test for Receiving

### Overview
Smart AUtest is an advanced automated testing suite designed to facilitate comprehensive testing with minimal setup. This case study focuses on MOCA-based test for the receiving process, specifically for identifying and processing incoming inventory using the provided Smart AUtest framework.

### Objective
To execute a MOCA-based test for receiving that simulates the identification and processing of incoming inventory, ensuring that the system accurately handles inventory data, including the generation of unique identifiers and the updating of relevant database tables.

### Have some samples created first
 
For inbound, we create sample RCVTRK data, for example RCVSMP001 

We have rcvtrk, rcvinv, rcvlin 

We could optionally have inventory as well for ASN testing 

### How we run a test 

For MOCA based test for receiving, we have truck and that is checked in as well, it will identify all inventory in the truck.  We have created this to support ASN scenario as well – so if truck inventory is already identified it simply returns success 

### Executing the run set 

We can execute the test by pressing the “Start” button 

![](Images/image10.png)

![](Images/image11.png)

For wh_id below script will call 

##publish data where @* and uc_use_context='rcvtrk' | Script("base_get_ossibot_wh_id")## 

We will give the our sample truck in uc_src_trknum, i.e. RCVSMP001 

And then we will press OK 

### Execution Console shows the execution 

The execution is displayed for each step: 
 - As it executes, the step we are executing is in yellow 
 - It shows status of each row 
 - It shows elapsed time for each row 
 
 ![](Images/image12.png)