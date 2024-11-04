### Overview

To execute a run set, select the desired run set and click Execute or start button. In this demonstration, we will be executing run set `BASE_INB_000000_CREATE_TO_DISPATCH`. 


### RUN Sets Steps

Following steps will be used in run set `BASE_INB_000000_CREATE_TO_DISPATCH`.

| **Step (Test)**                                        | **Description**                                                                                                                                                              |
|--------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001`      | This step copies a `RCVTRK` record and creates new `rcvtrk`, `rcvinv`, and `rcvlin` records for our test run. It utilizes the `uc_test_exec_seqnum` variable to ensure unique record creation. |
| `BASE_INB_0002100_TRLR_CKIN_MOCA_V001`                 | Using `uc_test_exec_seqnum`, this step checks in the truck against an open door.                                                                                             |
| `BASE_INB_0003100_IDENTIFY_MOCA_V001`                  | Now that we have a truck that is checked in as well, it will identify all inventory in the truck. We have created this to support ASN scenario as well – so if truck inventory is already identified it simply returns success. |
| `BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001` | We use this test twice and use test case concept. The first run moves inventory to receive stage and the next one will allocate a putaway location and drop it there. These steps support the concepts to run in a stress test mode as well. So when run normally, they will process everything in the truck. But when run in stress test mode they will process one record only. |
| `BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001`     | Closes and dispatches the truck.                                                                                                                                             |


### How Run Set will execute

Following steps will used to execute run set 

**Step:1**

Select the desired click on start button.

 <img src="./images/executions/Selectrunset.png" alt="undirectedmenu" style= "margin:auto;display:block">

**Step:2**
When we click on the execute button, we are asked to enter some arguments on the next screen, so we need to have some data (inbound order/ template) that we want to copy. We will enter values of that inbound order/template here and click ‘OK’.

 <img src="./images/executions/arguments.png" alt="undirectedmenu" style= "margin:auto;display:block">

After clicking OK, execution of run set will start.
-	See that wh_id is a script that calls:
```
##publish data where @* and uc_use_context='rcvtrk' | Script("base_get_ossibot_wh_id")##
``` 
-	And then we will press OK 

### Execution Console shows the execution 
The execution is displayed for each step: 
-	As it executes, the step we are executing is in yellow. 
-	It shows status of each row. 
-	It shows elapsed time for each row. 

When each row above is highlighted, the results associated with that specific MOCA snippet are displayed. This allows for an easy and direct examination of the outcomes linked to individual MOCA segments, ensuring clarity and facilitating a thorough review of the data provided in each snippet.

#### **Step:1**

This is showing result of BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001.
  
 <img src="./images/executions/copytemp_result.png" alt="undirectedmenu" style= "margin:auto;display:block">

#### **Step:2**

This is showing result of BASE_INB_0002100_TRLR_CKIN_MOCA_V001.


 <img src="./images/executions/IDNTIFY_RESULT.png" alt="undirectedmenu" style= "margin:auto;display:block">

#### **Step:3**

This is showing result of BASE_INB_0003100_IDENTIFY_MOCA_V001.


 <img src="./images/executions/trlrchkin_result.png" alt="undirectedmenu" style= "margin:auto;display:block">

#### **Step:4**

This is showing result of BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001.


 <img src="./images/executions/alloc_deposit_result.png.png" alt="undirectedmenu" style= "margin:auto;display:block">

#### **Step:5**

This is showing result of BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001.

 <img src="./images/executions/alloc_loc_result.png
 " alt="undirectedmenu" style= "margin:auto;display:block">

#### **Step:6**

This is showing result of BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001.

 <img src="./images/executions/close_dispatch_result.png" alt="undirectedmenu" style= "margin:auto;display:block">

As you can see from this illustration, highlighting each row above displays the results corresponding to that specific MOCA snippet. This makes the output of each command extremely useful in analysing the execution, as it allows for an easy and direct examination of the outcomes linked to individual MOCA segments. This approach ensures clarity and facilitates a thorough review of the data provided in each snippet.

### Execution Console also shows what was executed 

See the tab 'Commands on Target Env' 

 <img src="./images/executions/Results.png" alt="undirectedmenu" style= "margin:auto;display:block">

If you get an error, you can copy the 'command' from here and try running it directly 
