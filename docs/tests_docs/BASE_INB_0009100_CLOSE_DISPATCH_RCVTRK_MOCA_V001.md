# **BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001**


<!-- SMART_DOC_GEN_TEST_DESCR - Start -->
Close and dispatch receive trailer
<!-- SMART_DOC_GEN_TEST_DESCR - End -->

## **Test Category**

**☐** Custom  
**☐** Smart IS  
**🗹** Standard  

## **Overview**

In the described use case, the system is designed to manage the process of closing and dispatching a received truck, indicating a procedure that involves finalizing the receipt of goods from a truck and preparing it for dispatch to its next destination. This process likely includes verifying the received goods, updating inventory records, and preparing the truck for its next journey. 

Implementing this use case effectively requires a robust system for managing truck receipts and dispatches. It should be able to handle various scenarios, such as reconciling received goods with purchase orders, updating inventory levels accurately, and preparing the truck for dispatch in a timely manner. 

The system may also include features for tracking the status of received trucks, managing dock schedules, and coordinating with other systems or components involved in the receipt and dispatch process. This functionality is crucial for ensuring the smooth flow of goods through the warehouse or distribution center, minimizing delays, and maintaining accurate inventory records.

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
<tr><td>uc_new_trknum</td><td>Here you will give new truck num</td></tr>
<tr><td>uc_test_exec_seqnum</td><td>During each run, it generates a unique base-36 value.</td></tr>
<tr><td>wh_id</td><td>Warehouse ID</td></tr>
</table>
<!-- SMART_DOC_GEN_TEST_ARG - End -->

## **TestCases using this test**

This section provides a comprehensive list of test cases that are associated with this particular test. It provides a quick reference for understanding the specific tests covered. By reviewing these test cases, users can gain a deeper understanding of how this test is used in different scenarios and ensure comprehensive test coverage.


<!-- SMART_DOC_GEN_TEST_CASE_USING_THIS - Start -->
| Test Case ID | Test Case Description |
| ------------ | --------------------- |
| BASE_ALL_GEN | null |

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

The following steps represent a general procedure for dispatched order through GUI.

**Step:1**

Select **Configuration** > **Receiving**

![](BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001.png)

**Step:2**

Click on the **'Door Activity'** screen.

![](BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001/image2.png)

**Step:3**

Select the specific Dock Door and go to action close and dispatch trailor.

![](BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001/image3.png)


## **Applicable MOCA commands**

To dispatch order using the MOCA command, you can use the following command.

-  close trailer
-  process trailer dispatch


This command will trigger the dispatch order based on the predefined parameters and rules within the MOCA system.

## **Affected DB tables**

The following database table is typically affected while dispatching the order:

- **rcvtrk**
- **trlr**

These tables are likely to be affected to ensure proper tracking and management of the dispatch process and associated trucks.

---

**Previous-Test**
 [BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001](./tests_docs/BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001.md)
 
**Next-Test**
  [BASE_OUB_0020100_WAVE_PLAN_WEB_V001](./tests_docs/BASE_OUB_0020100_WAVE_PLAN_WEB_V001.md)
  
[SMART-IS](https://www.smart-is.pk) 