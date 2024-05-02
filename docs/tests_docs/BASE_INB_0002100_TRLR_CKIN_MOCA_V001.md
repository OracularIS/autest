# **BASE_INB_0002100_TRLR_CKIN_MOCA_V001**


<!-- SMART_DOC_GEN_TEST_DESCR - Start -->
Check in receive truck to an empty door
<!-- SMART_DOC_GEN_TEST_DESCR - End -->

## **Test Category**

<input type="checkbox" checked disabled> Standard
<br>
<input type="checkbox" disabled> Custom
<br>
<input type="checkbox" disabled> Smart IS

## **Overview**

In the described use case, the system is designed to manage the process of checking in transport equipment, indicating a procedure that involves registering the arrival of transport vehicles or equipment at a designated location, such as a warehouse or distribution center. This process likely includes verifying the identity of the transport equipment, inspecting it for any damage or defects, and recording its arrival for further processing.

Implementing this use case effectively requires a robust system for managing transport equipment check-ins. It should be able to handle various scenarios, such as different types of transport equipment, varying check-in procedures, and integration with other systems or components involved in the logistics process.

The system may also include features for tracking the status of transport equipment, managing parking or storage locations, and generating reports or notifications based on check-in events. This functionality is crucial for ensuring the efficient use of transport equipment, minimizing downtime, and maintaining a smooth flow of goods through the logistics network.

## **Applicable versions**

This test is designed to support versions greater than **2008.x.x**,
ensuring compatibility and smooth operation with the latest software
releases. Users can confidently utilize this test, as it is optimized
for newer versions while retaining a user-friendly testing process.

## **Test Arguments**

Test arguments are parameters or inputs that are passed to the test
cases to customize the test execution. These arguments providesss
flexibility and allow for the reuse of the same test case with different
sets of data or configurations. The input is as follows:


<!-- SMART_DOC_GEN_TEST_ARG - Start -->
<table>
<tr><th>Arguments</th><th>Argument Description</th></tr>
<tr><td>uc_new_trknum</td><td>Can pass a specific rcvtrk</td></tr>
<tr><td>uc_new_trknum_expr</td><td>Expression to build new truck number</td></tr>
<tr><td>uc_rcv_yard_loc_filter_expr</td><td>MOCA expression to find an empyty door</td></tr>
<tr><td>uc_test_exec_seqnum</td><td>During each run, it generates a unique base-36 value.</td></tr>
</table>
<!-- SMART_DOC_GEN_TEST_ARG - End -->

## **TestCases using this test**

This section provides a comprehensive list of test cases that are associated with this particular test. It provides a quick reference for understanding the specific tests covered. By reviewing these test cases, users can gain a deeper understanding of how this test is used in different scenarios and ensure comprehensive test coverage.


<!-- SMART_DOC_GEN_TEST_CASE_USING_THIS - Start -->
| Test Case ID | Test Case Description |
| ------------ | --------------------- |
| BASE_ALL_GEN |  |

<!-- SMART_DOC_GEN_TEST_CASE_USING_THIS - End -->

## **RunSets using this test**

This section details the various RunSets that utilize this test as part of their execution. Each RunSet represents a collection of tests and configurations that are executed together to achieve specific testing goals. By examining the RunSets that include this test, users can understand how it fits into larger testing scenarios and how it contributes to overall test coverage and automation.


<!-- SMART_DOC_GEN_RUN_SET_USING_THIS - Start -->
| Run Set ID | Run Set Description |
| ---------- | ------------------- |
| BASE_INB_000000_CREATE_TO_DISPATCH | This takes rcvtrk data, copies it, checks in, reeives, and dispatches |
| BASE_INB_000100_CREATE_TO_DISPATCH_USING_RF | Copy master receipt, identify putaway using RF |

<!-- SMART_DOC_GEN_RUN_SET_USING_THIS - End -->

## **Equivalent Usecase**

The following steps represent a general procedure for check IN through GUI.

**Step:1**

Select **Configuration** > **Receiving**

![](BASE_INB_0002100_TRLR_CKIN_MOCA_V001/image1.png)

**Step:2**

Click on the **'Check In'** screen.

![](BASE_INB_0002100_TRLR_CKIN_MOCA_V001/image2.png)

**Note:** You can check in with or without an appointment. If necessary, after viewing the Check In page, click Check in with appointment. If this option is not available, you are already in the correct check in mode.

**Step:3**

To change the selected appointment, click Select a different appointment, and then select a different appointment.

To change the appointment time:
    Click Change appointment time.
    In the Start Date and End Date fields, change the date and time of the appointment.
    Click Save.

![](BASE_INB_0002100_TRLR_CKIN_MOCA_V001/image3.png)


## **Applicable MOCA commands**

To dispatch order using the MOCA command, you can use the following command.

-  create trailer
-  change receive truck
-  process trailer dispatch


This command will trigger the check in based on the predefined parameters and rules within the MOCA system.

## **Affected DB tables**

The following database table is typically affected while check IN:

- **rcvtrk**
- **trlr**

These tables are likely to be affected to ensure proper tracking and management of the check in trailors.

---
 **Previous-Test**
 [BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001.md)
 
 **Next-Test**
  [BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001](./tests_docs/BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001.md)
  
[SMART-IS](https://www.smart-is.pk) 