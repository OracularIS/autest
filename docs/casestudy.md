# Case Study

## MOCA Based Test for Receiving

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

### Executing the test

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

 
## RF Based Test for Receiving

### Overview
Smart AUtest is an advanced automated testing suite designed to facilitate comprehensive testing with minimal setup. This case study focuses on RF-based test for the receiving process, specifically for identifying and processing incoming inventory using the provided Smart AUtest framework.

### Objective
To execute a RF-based test for receiving that simulates the identification and processing of incoming inventory, ensuring that the system accurately handles inventory data, including the generation of unique identifiers and the updating of relevant database tables.

### Have some samples created first
 
For inbound, we create sample RCVTRK data, for example RCVSMP001 

We have rcvtrk, rcvinv, rcvlin 

We could optionally have inventory as well for ASN testing 

### How we run a test 

For RF based test for receiving, we have truck and that is checked in as well, it will identify all inventory in the truck.  We have created this to support ASN scenario as well – so if truck inventory is already identified it simply returns success 

### Executing the test 

We can execute the test by pressing the “Start” button 

![](Images/image13.png)

![](Images/image14.png)

For rcv_id below expression will execute

[['ARTRK-' || '@uc_test_exec_seqnum']] 

### Execution Console shows the execution 

The execution is displayed for each step: 
 - As it executes, the step we are executing is in yellow 
 - It shows status of each row 
 - It shows elapsed time for each row 


## Web Based Test for Wave Planning 

### Overview

Smart AUtest is an advanced automated testing suite designed to facilitate comprehensive testing with minimal setup. This case study focuses on web-based testing for the wave planning process, specifically for organizing and optimizing order fulfillment using the provided Smart AUtest framework.

### Objective

To execute a web-based test for wave planning that simulates the organization and optimization of order fulfillment, ensuring that the system accurately groups and prioritizes orders, generates efficient picking plans, and updates relevant database tables accordingly.

### Have some samples created first
 
For outbound we create orders  

 - Template_flg = 1 
 - Orders are named with “ATST-TMPL-“ prefix. 
 - We have orders and order line data. 

### Executing the test 

We can execute the test by pressing the “Start” button 

![](Images/image15.png)

![](Images/image16.png)


### Execution Console shows the execution 

The execution is displayed for each step: 
 - As it executes, the step we are executing is in yellow 
 - It shows status of each row 
 - It shows elapsed time for each row 

## Run Set for RF receiving

### Overview
Smart AUtest is an advanced automated testing suite designed to facilitate comprehensive testing with minimal setup. This case study focuses on run set of RF-based tests for the receiving process, specifically aimed at verifying the identification and processing of incoming inventory using the provided Smart AUtest framework.

### Objective
To execute a run set of RF-based tests for receiving that simulates the identification and processing of incoming inventory. The tests aim to ensure that the system accurately identifies inventory, processes incoming items efficiently, and updates the relevant database tables. This includes scenarios where the truck inventory is already identified, supporting ASN processes by returning success if inventory identification is pre-existing.

### Have some samples created first 

For inbound, we create sample RCVTRK data, for example RCVSMP001

We have rcvtrk, rcvinv, rcvlin

We could optionally have inventory as well for ASN testing 


### The final run set defines how we run this 

For this illustration, see BASE_INB_000100_CREATE_TO_DISPATCH_USING_RF run set.  This has following steps for the run set: 
Sure, here's the information in a tabular format using Markdown:

| **Step (Test)**                           | **Description**                                                                                                                                                              |
|-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001` | This step copies a `RCVTRK` record and creates a new `rcvtrk`, `rcvinv`, `rcvlin` for our run. It will use the `uc_test_exec_seqnum` variable (set by the framework) to help in creating a new `rcvtrk`. |
| `BASE_INB_0002100_TRLR_CKIN_MOCA_V001`    | We have `uc_test_exec_seqnum`, so it uses that to find the data we created. It then checks in the truck against an open door.                                                  |
| `BASE_INB_0003200_IDENTIFY_RF_V001`       | Now that we have the truck checked in, it will identify all inventory in the truck. This supports the ASN scenario as well – if truck inventory is already identified, it simply returns success. |
| `BASE_INV_0020100_MOVE_RF_V001`           | This will move inventory to the destination location.                                                                                                                         |
| `BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001` | This step will close and dispatch the truck we just created.                                                                                                                   |

### Executing the run set 

We can execute the run set by pressing the “Start” button 

![](Images/image20.png)

![](Images/image21.png)


See that wh_id is a script that calls: 

##publish data where @* and uc_use_context='rcvtrk' | Script("base_get_ossibot_wh_id")## 

We will give the our sample truck in uc_src_trknum, i.e. RCVSMP001 

And then we will press OK 

### Execution Console shows the execution 

The execution is displayed for each step: 

 - As it executes, the step we are executing is in yellow 

 - It shows status of each row 

 - It shows elapsed time for each row 



