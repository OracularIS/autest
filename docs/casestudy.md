# Case Study

## MOCA Based Test for Receiving

### Overview
Smart AUtest is an advanced automated testing suite designed to facilitate comprehensive testing with minimal setup. This case study focuses on MOCA-based tests for the receiving process, specifically for identifying and processing incoming inventory using the provided Smart AUtest framework.

### Objective
The primary objective of this case study is to execute a MOCA-based test for receiving that simulates the identification and processing of incoming inventory. The goal is to ensure that the system accurately handles inventory data, including the generation of unique identifiers and the updating of relevant database tables.

### Sample Data Creation

**Sample RCVTRK Data**
For the purpose of testing inbound inventory, we create sample RCVTRK data. For example, we use the identifier **RCVSMP001** to represent a sample truck. This data will be utilized to simulate the presence of incoming inventory on a truck.

**Relevant Tables**
- **rcvtrk**: This table contains information about the trucks and their status.
- **rcvinv**: This table contains information about the inventory received.
- **rcvlin**: This table contains line items related to the received inventory.

Optionally, we can include inventory data for ASN testing.

### Running the Test

#### MOCA-Based Test for Receiving
For the MOCA-based test for receiving, we assume a scenario where a truck has arrived and has been checked in. The system will identify all inventory items on the truck. This setup supports ASN scenarios, ensuring that if the truck's inventory is already identified, the test simply returns a success status.

#### Execution Steps

1. **Initiating the Test**
   - To execute the test, press the “Start” button on the Smart AUtest interface.
   - ![](Images/image10.png)
   - ![](Images/image11.png)

2. **Script Execution for Warehouse Identification**
   - The following script will be called to identify the warehouse ID:
     ```
     ##publish data where @* and uc_use_context='rcvtrk' | Script("base_get_ossibot_wh_id")##
     ```
   - In this script, we will input our sample truck identifier in the variable `uc_src_trknum`, i.e., `RCVSMP001`.

3. **Confirming the Sample Truck**
   - After entering the truck identifier, press "OK" to proceed.

### Execution Console

The execution console provides real-time feedback on the test process. Key features include:

- **Step Highlighting**: The current step being executed is highlighted in yellow.
- **Status Display**: Each row's status is displayed, indicating success or failure.
- **Elapsed Time**: The elapsed time for each row is shown, providing insight into the test duration.
  
  ![](Images/image12.png)

### Detailed Execution Flow

1. **Start Button Pressed**:
   - The test initiates upon pressing the "Start" button.
   - The system begins by verifying the presence of the sample truck (`RCVSMP001`) in the `rcvtrk` table.

2. **Warehouse ID Retrieval**:
   - The script `##publish data where @* and uc_use_context='rcvtrk' | Script("base_get_ossibot_wh_id")## ` is executed, fetching the warehouse ID where the truck 
     is supposed to be received.
   - This ensures that the system is contextually aware of the warehouse environment.

3. **Inventory Identification**:
   - The system then moves to identify all inventory items associated with the truck. This includes checking the `rcvinv` and `rcvlin` tables.
   - If the inventory has already been identified (supporting ASN scenarios), the test will return a success status without re-processing the inventory.

4. **Database Updates**:
   - Unique identifiers for the received inventory are generated.
   - Relevant database tables (`rcvtrk`, `rcvinv`, `rcvlin`) are updated with the latest inventory data.

5. **Completion**:
   - The execution console displays each step, with the current step highlighted.
   - Status and elapsed time for each row are shown, providing a clear overview of the test progress and performance.
 
## RF Based Test for Receiving

## RF-Based Test for Receiving

### Overview
Smart AUtest is an advanced automated testing suite designed to facilitate comprehensive testing with minimal setup. This case study focuses on RF-based tests for the receiving process, specifically for identifying and processing incoming inventory using the provided Smart AUtest framework.

### Objective
The primary objective of this case study is to execute an RF-based test for receiving that simulates the identification and processing of incoming inventory. The goal is to ensure that the system accurately handles inventory data, including the generation of unique identifiers and the updating of relevant database tables.

### Sample Data Creation

**Sample RCVTRK Data**
For the purpose of testing inbound inventory, we create sample RCVTRK data. For example, we use the identifier **RCVSMP001** to represent a sample truck. This data will be utilized to simulate the presence of incoming inventory on a truck.

** Relevant Tables**
- **rcvtrk**: This table contains information about the trucks and their status.
- **rcvinv**: This table contains information about the inventory received.
- **rcvlin**: This table contains line items related to the received inventory.

Optionally, we can include inventory data for Advanced Shipping Notice (ASN) testing.

### Running the Test

#### RF-Based Test for Receiving
For the RF-based test for receiving, we assume a scenario where a truck has arrived and has been checked in. The system will identify all inventory items on the truck. This setup supports ASN scenarios, ensuring that if the truck's inventory is already identified, the test simply returns a success status.

#### Execution Steps

1. **Initiating the Test**
   - To execute the test, press the “Start” button on the Smart AUtest interface.
   - ![](Images/image13.png)
   - ![](Images/image14.png)

2. **Script Execution for RCV_ID Generation**
   - The following expression will be executed to generate the `rcv_id`:
     ```sql
     [['ARTRK-' || '@uc_test_exec_seqnum']]
     ```
   - This expression concatenates the prefix `ARTRK-` with the unique test execution sequence number, ensuring a unique identifier for each test run.

3. **Confirming the Sample Truck**
   - After generating the `rcv_id`, the system will use this identifier to track the sample truck (`RCVSMP001`) in the `rcvtrk` table.

### Execution Console

The execution console provides real-time feedback on the test process. Key features include:

- **Step Highlighting**: The current step being executed is highlighted in yellow.
- **Status Display**: Each row's status is displayed, indicating success or failure.
- **Elapsed Time**: The elapsed time for each row is shown, providing insight into the test duration.
  
  ![](Images/image12.png)

### Detailed Execution Flow

1. **Start Button Pressed**:
   - The test initiates upon pressing the "Start" button.
   - The system begins by verifying the presence of the sample truck (`RCVSMP001`) in the `rcvtrk` table.

2. **RCV_ID Generation**:
   - The expression `[['ARTRK-' || '@uc_test_exec_seqnum']]` is executed to generate a unique `rcv_id`.
   - This `rcv_id` is used to uniquely identify the test run and associate it with the specific truck and its inventory.

3. **Inventory Identification**:
   - The system then moves to identify all inventory items associated with the truck. This includes checking the `rcvinv` and `rcvlin` tables.
   - If the inventory has already been identified (supporting ASN scenarios), the test will return a success status without re-processing the inventory.

4. **Database Updates**:
   - Unique identifiers for the received inventory are generated.
   - Relevant database tables (`rcvtrk`, `rcvinv`, `rcvlin`) are updated with the latest inventory data.

5. **Completion**:
   - The execution console displays each step, with the current step highlighted.
   - Status and elapsed time for each row are shown, providing a clear overview of the test progress and performance.


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

Then here we have to provide URL and press OK to start the test.

![](Images/image17.png)


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

### Steps execute

Below steps will execute for this runset

![](Images/image22.png)

