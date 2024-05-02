# **BASE_OUB_0050000_LIST_PICK_MOCA_V001**


<!-- SMART_DOC_GEN_TEST_DESCR - Start -->
This tests builds upon other BASE outboudn tests.  It would do list picking for those orders using standard MOCA Commands.
<!-- SMART_DOC_GEN_TEST_DESCR - End -->

## **Test Category**

<input type="checkbox" checked disabled> Standard
<br>
<input type="checkbox" disabled> Custom
<br>
<input type="checkbox" disabled> Smart IS


## **Overview**

List picking in Blue Yonder warehouse management system typically involves the process of fulfilling customer orders by selecting and collecting items from the warehouse based on a generated picking list. This list is dynamically created, considering factors such as inventory levels, order priorities, and optimal picking routes. The software aims to optimize the efficiency of the picking process by organizing items in a logical sequence, reducing travel time for warehouse personnel.

Additionally, Blue Yonder system often incorporates features like barcode scanning and real-time inventory updates to enhance accuracy and streamline the overall order fulfillment process, contributing to improved customer satisfaction and operational effectiveness.

**Applicable versions**

This test is designed to support versions greater than 2008.x.x, ensuring compatibility and smooth operation with the latest software releases. Users can confidently utilize this test, as it is optimized for newer versions while retaining a user-friendly testing process.

**Test Arguments**

Test arguments are parameters or inputs that are passed to the test
cases to customize the test execution. These arguments provide
flexibility and allow for the reuse of the same test case with different
sets of data or configurations. The input is as follows:


<!-- SMART_DOC_GEN_TEST_ARG - Start -->
<table>
<tr><th>Arguments</th><th>Argument Description</th></tr>
<tr><td>dstlod</td><td>Which load to pick to.  By default, use "ALD" || @uc_test_exec_seqnum || "AA" || @list_id</td></tr>
<tr><td>list_id</td><td>You can also explicitly pass in a list ID if needed for operations</td></tr>
<tr><td>uc_get_srclod_cmd</td><td> Determine the command to fetch source inventory. The default is a standard command that lists available inventory for pick in a specific location.</td></tr>
<tr><td>uc_list_id_filter_sql</td><td>A filter to make sure we run our list only</td></tr>
<tr><td>uc_move_to_next_hop</td><td>If set to "1", we will move to the first destination in the workflow automatically</td></tr>
<tr><td>uc_test_exec_seqnum</td><td>During each run, it generates unique base-36 value.</td></tr>
<tr><td>uc_tmp_pckloc</td><td>Specify the location from which you want to pick items</td></tr>
<tr><td>uc_wave_set_expr</td><td>To locate data for the test run, set a default wave set. Default is as we used during order creation, i.e. "AW" || @uc_test_exec_seqnum</td></tr>
<tr><td>wave_set</td><td>you can explicitly pass in a wave set for specific cases</td></tr>
</table>
<!-- SMART_DOC_GEN_TEST_ARG - End -->

## **TestCases using this test**

This section provides a comprehensive list of test cases that are associated with this particular test. It provides a quick reference for understanding the specific tests covered. By reviewing these test cases, users can gain a deeper understanding of how this test is used in different scenarios and ensure comprehensive test coverage.


<!-- SMART_DOC_GEN_TEST_CASE_USING_THIS - Start -->
| Test Case ID | Test Case Description |
| ------------ | --------------------- |

<!-- SMART_DOC_GEN_TEST_CASE_USING_THIS - End -->

## **RunSets using this test**

This section details the various RunSets that utilize this test as part of their execution. Each RunSet represents a collection of tests and configurations that are executed together to achieve specific testing goals. By examining the RunSets that include this test, users can understand how it fits into larger testing scenarios and how it contributes to overall test coverage and automation.


<!-- SMART_DOC_GEN_RUN_SET_USING_THIS - Start -->
| Run Set ID | Run Set Description |
| ---------- | ------------------- |
| BASE_OUB_000000_CREATE_TO_DISPATCH | create order, plan, allocate, release, pick, dispatch |
| BASE_OUB_001000_TRAFFIC_PLAN_CREATE_TO_DISPATCH | create order, plan, allocate, release, pick, dispatch |

<!-- SMART_DOC_GEN_RUN_SET_USING_THIS - End -->

## **Equivalent Usecase**

The following steps represent a general procedure for list Picking through GUI.

**Step:1**

Select **Configuration** > **Picking**

![](BASE_OUB_0050000_LIST_PICK_MOCA_V001/image1.png)

**Step:2**

Click on the **'pick confirmation'** screen.

![](BASE_OUB_0050000_LIST_PICK_MOCA_V001/image2.png)


**Step:3**

Click on **quick filter** tab.

![](BASE_OUB_0050000_LIST_PICK_MOCA_V001/image3.png)


**Step:4**


Go to the '**Actions**' tab and click on 'Confirm Picks'.

![](BASE_OUB_0050000_LIST_PICK_MOCA_V001/image4.png)


**Step:5**

Pick Confirmation Screen will open and the Press **Confirm Pick**


## **Applicable MOCA commands**

For list pick using the MOCA command, you can use the following command.

-   **List available inventory for pick in location**


This command will perform list picking and this command is based on the predefined parameters and rules within the MOCA system.

## **Affected DB Tables**

When list pick action performs, the following database tables are typically affected:

-   **Pcklst**

-   **Pckwrk_view**

-   **Wrkque**

-   **Ord_line**

These tables are crucial for list picking within the warehouse management system.

---

 **Previous-Test**
 [BASE_OUB_0040000_WAIT_REL_MOCA_V001](./tests_docs/BASE_OUB_0040000_WAIT_REL_MOCA_V001.md)
 
**Next-Test**
  [BASE_OUB_0060000_PICK_HOP_MOCA_V001](./tests_docs/BASE_OUB_0060000_PICK_HOP_MOCA_V001.md)

[SMART-IS](https://www.smart-is.pk) 