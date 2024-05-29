# Case Study

## MOCA Based Test for Receiving

### Overview
Smart AUtest is an advanced automated testing suite designed to facilitate comprehensive testing with minimal setup. This case study focuses on MOCA-based tests for the receiving process, specifically for identifying and processing incoming inventory using the provided Smart AUtest framework.

### Objective
The primary objective of this case study is to execute a MOCA-based test for receiving that simulates the identification and processing of incoming inventory. The goal is to ensure that the system accurately handles inventory data, including the generation of unique identifiers and the updating of relevant database tables.

### How to Create MOCA Based Test


Creating MOCA-based tests involves several steps, including configuring the test environment, writing the test scripts, and validating the test results. Detailed instructions can be found in the [Creating MOCA Based Test](./Creating_Tests.md#Creating-MOCA-Based-Tests) documentation. Below is a brief overview of the process:

1. **Configure Test Environment**: Set up the test environment by defining the necessary configurations and parameters required for the test.
2. **Write Test Scripts**: Develop the MOCA scripts to simulate the desired test scenarios. These scripts will interact with the database and perform various operations such as data retrieval and updates.
3. **Validate Test Results**: Execute the test scripts and validate the results to ensure that the test objectives are met. Check the database tables and other output to confirm that the inventory data has been correctly processed.


### Sample Data Creation

**Sample RCVTRK Data**

For the purpose of testing inbound inventory, we create sample RCVTRK data. For example, we use the identifier **RCVSMP001** to represent a sample truck. This data will be utilized to simulate the presence of incoming inventory on a truck.

**Relevant Tables**

- **rcvtrk**: This table contains information about the trucks and their status.
- **rcvinv**: This table contains information about the inventory received.
- **rcvlin**: This table contains line items related to the received inventory.

Optionally, we can include inventory data for ASN testing.

For detailed information on available tests, refer to the [Packaged Tests](./packaged_tests.md) documentation

### Running the Test

**MOCA-Based Test for Receiving**

For the MOCA-based test for receiving, we assume a scenario where a truck has arrived and has been checked in. The system will identify all inventory items on the truck. This setup supports ASN scenarios, ensuring that if the truck's inventory is already identified, the test simply returns a success status.

**Execution Steps**

1. **Initiating the Test**
   - Open the Smart AUtest interface.
   - Press the “Start” button to initiate the test.

     ![](Images/image10.png)

     ![](Images/image11.png)

3. **Script Execution for Warehouse Identification**
   
   - The system will execute the following script to identify the warehouse ID:
     ```
     ##publish data where @* and uc_use_context='rcvtrk' | Script("base_get_ossibot_wh_id")##
     ```
   - In this script, we will input our sample truck identifier in the variable `uc_src_trknum`, i.e., `RCVSMP001`.

4. **Confirming the Sample Truck**
   
   - After entering the truck identifier, press "OK" to proceed.

### Execution Console

The execution console provides real-time feedback on the test process. Key features include:

- **Step Highlighting**: The current step being executed is highlighted in yellow.
- **Status Display**: Each row's status is displayed, indicating success or failure.
- **Elapsed Time**: The elapsed time for each row is shown, providing insight into the test duration.

![](Images/image50.png)


### Detailed Execution Flow

1. **Start Button Pressed**:
   - The test initiates upon pressing the "Start" button.
   - The system begins by verifying the presence of the sample truck (`RCVSMP001`) in the `rcvtrk` table. If the truck is not found, the test will fail at this step.

2. **Warehouse ID Retrieval**:
   - The script `##publish data where @* and uc_use_context='rcvtrk' | Script("base_get_ossibot_wh_id")## ` is executed.
   - This script fetches the warehouse ID where the truck is supposed to be received, ensuring that the system is contextually aware of the warehouse environment. The warehouse ID is crucial for subsequent steps to correctly process the inventory.

3. **Inventory Identification**:
   - The system moves to identify all inventory items associated with the truck. This includes querying the `rcvinv` and `rcvlin` tables to retrieve inventory details.
   - If the inventory has already been identified (supporting ASN scenarios), the test will return a success status without re-processing the inventory.
   - The script validates the presence and status of the inventory items, ensuring they match the expected data for the sample truck.

4. **Database Updates**:
   - Unique identifiers for the received inventory are generated. This step ensures that each item is uniquely tracked within the system.
   - The system updates the relevant database tables (`rcvtrk`, `rcvinv`, `rcvlin`) with the latest inventory data, reflecting the current status of the truck and its cargo.
   - The script ensures that all necessary fields in the database tables are correctly populated, maintaining data integrity and accuracy.

5. **Completion**:
   - The execution console displays each step of the process, with the current step highlighted for easy tracking.
   - The status (success or failure) and elapsed time for each row are shown, providing a clear overview of the test progress and performance.
   - On completion, the test provides a detailed report, including any discrepancies or errors encountered during the execution.

### Conclusion

This case study demonstrates the effectiveness of Smart AUtest in executing MOCA-based tests for the receiving process. By simulating the identification and processing of incoming inventory, the system ensures accurate handling of inventory data, generation of unique identifiers, and updating of relevant database tables. This process not only verifies the system's functionality but also enhances the reliability and efficiency of inventory management.

### Recommendations

- **Regular Testing**: Implement regular testing schedules to ensure ongoing accuracy and reliability of the receiving process.
- **Data Validation**: Continuously validate sample data and test scripts to reflect any changes in the inventory process or database schema.
- **Enhanced Reporting**: Utilize detailed test reports to identify and address any issues promptly, ensuring smooth operations.

By following these recommendations and utilizing the comprehensive testing capabilities of Smart AUtest, organizations can significantly improve their inventory management processes and ensure seamless operations in their receiving departments.
 
## RF Based Test for Receiving

### Overview

Smart AUtest is an advanced automated testing suite designed to facilitate comprehensive testing with minimal setup. This case study focuses on RF-based tests for the receiving process, specifically for identifying and processing incoming inventory using the Smart AUtest framework.

### Objective

The primary objective of this case study is to execute an RF-based test for receiving that simulates the identification and processing of incoming inventory. The goal is to ensure that the system accurately handles inventory data, including the generation of unique identifiers and the updating of relevant database tables.

### Sample Data Creation

**Sample RCVTRK Data**

For the purpose of testing inbound inventory, we create sample RCVTRK data. For example, we use the identifier **RCVSMP001** to represent a sample truck. This data simulates the presence of incoming inventory on a truck.

**Relevant Tables**

- **rcvtrk**: Contains information about the trucks and their status.
- **rcvinv**: Contains information about the inventory received.
- **rcvlin**: Contains line items related to the received inventory.

Optionally, inventory data for Advanced Shipping Notice (ASN) testing can be included to simulate scenarios where the inventory details are already known before the truck arrives.

For detailed information on available tests, refer to the [Packaged Tests](./packaged_tests.md) documentation


### Running the Test

**RF Based Test for Receiving**

We will assume a scenario where a truck has arrived and has been checked in. The system will identify all inventory items on the truck. This setup supports ASN scenarios, ensuring that if the truck's inventory is already identified, the test simply returns a success status.

**Execution Steps**

1. **Initiating the Test**
   - Open the Smart AUtest interface.
   - Press the “Start” button to initiate the test.

     ![](Images/image13.png)

     ![](Images/image14.png)

2. **Script Execution for RCV_ID Generation**
   - The system will execute the following expression to generate the `rcv_id`:
     ```
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

### Detailed Execution Flow

1. **Start Button Pressed**:
   - The test initiates upon pressing the "Start" button.
   - The system begins by verifying the presence of the sample truck (`RCVSMP001`) in the `rcvtrk` table. If the truck is not found, the test will fail at this step.

2. **RCV_ID Generation**:
   - The expression `[['ARTRK-' || '@uc_test_exec_seqnum']]` is executed to generate a unique `rcv_id`.
   - This `rcv_id` is used to uniquely identify the test run and associate it with the specific truck and its inventory. It ensures traceability and helps in tracking the inventory through the system.

3. **Inventory Identification**:
   - The system moves to identify all inventory items associated with the truck. This includes querying the `rcvinv` and `rcvlin` tables to retrieve inventory details.
   - If the inventory has already been identified (supporting ASN scenarios), the test will return a success status without re-processing the inventory.
   - The script validates the presence and status of the inventory items, ensuring they match the expected data for the sample truck.

4. **Database Updates**:
   - Unique identifiers for the received inventory are generated. This step ensures that each item is uniquely tracked within the system.
   - The system updates the relevant database tables (`rcvtrk`, `rcvinv`, `rcvlin`) with the latest inventory data, reflecting the current status of the truck and its cargo.
   - The script ensures that all necessary fields in the database tables are correctly populated, maintaining data integrity and accuracy.

5. **Completion**:
   - The execution console displays each step of the process, with the current step highlighted for easy tracking.
   - The status (success or failure) and elapsed time for each row are shown, providing a clear overview of the test progress and performance.
   - On completion, the test provides a detailed report, including any discrepancies or errors encountered during the execution.

### Conclusion

This case study demonstrates the effectiveness of Smart AUtest in executing RF-based tests for the receiving process. By simulating the identification and processing of incoming inventory, the system ensures accurate handling of inventory data, generation of unique identifiers, and updating of relevant database tables. This process not only verifies the system's functionality but also enhances the reliability and efficiency of inventory management.

### Recommendations

- **Regular Testing**: Implement regular testing schedules to ensure ongoing accuracy and reliability of the receiving process.
- **Data Validation**: Continuously validate sample data and test scripts to reflect any changes in the inventory process or database schema.
- **Enhanced Reporting**: Utilize detailed test reports to identify and address any issues promptly, ensuring smooth operations.

By following these recommendations and utilizing the comprehensive testing capabilities of Smart AUtest, organizations can significantly improve their inventory management processes and ensure seamless operations in their receiving departments.

## Web Based Test for Wave Planning

### Overview

Smart AUtest is an advanced automated testing suite designed to facilitate comprehensive testing with minimal setup. This case study focuses on web-based testing for the wave planning process, specifically for organizing and optimizing order fulfillment using the Smart AUtest framework.

### Objective

The primary objective of this case study is to execute a web-based test for wave planning that simulates the organization and optimization of order fulfillment. The goal is to ensure that the system accurately groups and prioritizes orders, generates efficient picking plans, and updates relevant database tables accordingly.

### Sample Data Creation

For the purpose of testing wave planning, we create sample orders with the following criteria:
- **Template_flg = 1**: Indicates that these orders are templates for generating actual orders.
- Orders are named with a **“ATST-TMPL-“** prefix.
- We generate both orders and order line data to simulate a realistic scenario.

For detailed information on available tests, refer to the [Packaged Tests](./packaged_tests.md) documentation


### Running the Test

**Executing the Test**

To execute the test, follow these steps:

1. **Initiating the Test**
   - Open the Smart AUtest interface.
   - Press the “Start” button to initiate the test.

     ![](Images/image15.png)

     ![](Images/image16.png)

2. **URL Prompt**
   - After pressing the "Start" button, a prompt will appear requesting the URL for the web-based wave planning module.
   - Enter the URL and press "OK" to start the test.

     ![](Images/image17.png)

### Execution Console

The execution console provides real-time feedback on the test process. Key features include:

- **Step Highlighting**: The current step being executed is highlighted in yellow.
- **Status Display**: Each row's status is displayed, indicating success or failure.
- **Elapsed Time**: The elapsed time for each row is shown, providing insight into the test duration.


### Detailed Execution Flow

1. **Start Button Pressed**:
   - The test initiates upon pressing the "Start" button.
   - The system begins by loading the web-based wave planning module.

2. **URL Prompt**:
   - After initiating the test, a prompt appears requesting the URL.
   - Enter the URL for the wave planning module and confirm to proceed with the test.

3. **Wave Planning Execution**:
   - The system simulates the wave planning process, which involves organizing and optimizing order fulfillment.
   - Orders are grouped and prioritized based on predefined criteria.
   - Efficient picking plans are generated to streamline the fulfillment process.
   - The system simulates user interactions with the web interface, ensuring the correct execution of wave planning activities.

4. **Database Updates**:
   - Relevant database tables are updated to reflect the changes made during wave planning.
   - This includes updating order statuses, generating picking lists, and recording any modifications to order details.
   - The system ensures that all changes are accurately recorded in the database, maintaining data integrity and consistency.

5. **Completion**:
   - The execution console displays each step of the process, with the current step highlighted for easy tracking.
   - The status (success or failure) and elapsed time for each row are shown, providing a clear overview of the test progress and performance.
   - On completion, the test provides a detailed report, including any discrepancies or errors encountered during the execution.

### Conclusion

This case study demonstrates the effectiveness of Smart AUtest in executing web-based tests for the wave planning process. By simulating the organization and optimization of order fulfillment, the system ensures accurate grouping and prioritization of orders, generation of efficient picking plans, and updating of relevant database tables. This process not only verifies the system's functionality but also enhances the reliability and efficiency of order fulfillment operations.

### Recommendations

- **Regular Testing**: Implement regular testing schedules to ensure ongoing accuracy and reliability of the wave planning process.
- **Data Validation**: Continuously validate sample data and test scripts to reflect any changes in the wave planning process or database schema.
- **Enhanced Reporting**: Utilize detailed test reports to identify and address any issues promptly, ensuring smooth operations.

By following these recommendations and utilizing the comprehensive testing capabilities of Smart AUtest, organizations can significantly improve their order fulfillment processes and ensure seamless operations in their wave planning departments.

## Run Set for RF Receiving

### Overview

Smart AUtest is an advanced automated testing suite designed to facilitate comprehensive testing with minimal setup. This case study focuses on a run set of RF-based tests for the receiving process, specifically aimed at verifying the identification and processing of incoming inventory using the Smart AUtest framework.

### Objective

The objective of this run set is to execute a series of RF-based tests for receiving to simulate the identification and processing of incoming inventory. The tests aim to ensure that the system accurately identifies inventory, processes incoming items efficiently, and updates the relevant database tables. This includes scenarios where the truck inventory is already identified, supporting Advanced Shipping Notice (ASN) processes by returning success if inventory identification is pre-existing.

### Sample Data Creation

For inbound testing, we create sample RCVTRK data, using identifiers such as **RCVSMP001**. This data includes records in the following tables:

- **rcvtrk**: Contains information about the trucks and their status.
- **rcvinv**: Contains information about the inventory received.
- **rcvlin**: Contains line items related to the received inventory.

Optionally, inventory data can be included for ASN testing to simulate scenarios where the inventory details are already known before the truck arrives.
For detailed information on available tests, refer to the [Packaged Tests](./packaged_tests.md) documentation

### Run Set Definition

For this illustration, we use the `BASE_INB_000100_CREATE_TO_DISPATCH_USING_RF` run set, which consists of the following steps:

| **Step (Test)**                             | **Description**                                                                                                                                                              |
|---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001` | This step copies a `RCVTRK` record and creates new `rcvtrk`, `rcvinv`, and `rcvlin` records for our test run. It utilizes the `uc_test_exec_seqnum` variable to ensure unique record creation. |
| `BASE_INB_0002100_TRLR_CKIN_MOCA_V001`    | Using `uc_test_exec_seqnum`, this step checks in the truck against an open door.                                                                                            |
| `BASE_INB_0003200_IDENTIFY_RF_V001`       | Identifies all inventory in the truck. Supports ASN scenarios, returning success if truck inventory is already identified.                                                    |
| `BASE_INV_0020100_MOVE_RF_V001`           | Moves inventory to the destination location.                                                                                                                                  |
| `BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001` | Closes and dispatches the truck.                                                                                                                                             |

### Executing the Run Set

**Initiating the Test**

To execute the run set, follow these steps:

1. **Press the "Start" Button**
   - Open the Smart AUtest interface.
   - Press the “Start” button to initiate the test.

     ![](Images/image20.png)

     ![](Images/image21.png)

2. **Provide Required Information**
   - Enter the sample truck identifier (`RCVSMP001`) when prompted.
   - Press "OK" to proceed with the execution.

**Execution Console**

The execution console provides real-time feedback on the test process, displaying each step as it executes. Key features include:

- **Step Highlighting**: The currently executing step is highlighted in yellow.
- **Status Display**: Each row's status is shown, indicating success or failure.
- **Elapsed Time**: The time taken for each step is displayed, providing insights into test duration and performance.


### Detailed Execution Flow

The following steps are executed as part of this run set:

1. **Step: `BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001`**
   - This step copies a `RCVTRK` record and creates new `rcvtrk`, `rcvinv`, and `rcvlin` records for the test run.
   - It utilizes the `uc_test_exec_seqnum` variable to ensure unique record creation.
   - This step ensures that the test has a fresh set of data to work with, simulating a real scenario of incoming inventory.

2. **Step: `BASE_INB_0002100_TRLR_CKIN_MOCA_V001`**
   - This step checks in the truck using the `uc_test_exec_seqnum` variable against an open door.
   - The system verifies that the truck (`RCVSMP001`) is checked in correctly, updating the `rcvtrk` table to reflect the check-in status.

3. **Step: `BASE_INB_0003200_IDENTIFY_RF_V001`**
   - This step identifies all inventory in the truck.
   - Supports ASN scenarios by returning success if the truck inventory is already identified.
   - The system ensures that all items in the truck are accounted for and updates the `rcvinv` and `rcvlin` tables accordingly.

4. **Step: `BASE_INV_0020100_MOVE_RF_V001`**
   - This step moves inventory to the destination location.
   - It simulates the physical movement of inventory within the warehouse, updating the system to reflect the new locations of the items.

5. **Step: `BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001`**
   - This step closes and dispatches the truck.
   - The system updates the `rcvtrk` table to reflect the dispatch status, completing the receiving process.

![](Images/image22.png)

### Conclusion

This case study demonstrates the effectiveness of Smart AUtest in executing a run set of RF-based tests for the receiving process. By simulating the identification and processing of incoming inventory, the system ensures accurate handling of inventory data, efficient processing of items, and updating of relevant database tables. This comprehensive testing approach verifies the system's functionality and enhances the reliability and efficiency of inventory management.

### Recommendations

- **Regular Testing**: Implement regular testing schedules to ensure ongoing accuracy and reliability of the receiving process.
- **Data Validation**: Continuously validate sample data and test scripts to reflect any changes in the inventory process or database schema.
- **Enhanced Reporting**: Utilize detailed test reports to identify and address any issues promptly, ensuring smooth operations.

By following these recommendations and utilizing the comprehensive testing capabilities of Smart AUtest, organizations can significantly improve their inventory management processes and ensure seamless operations in their receiving departments.
