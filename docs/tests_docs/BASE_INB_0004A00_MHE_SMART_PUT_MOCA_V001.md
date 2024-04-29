# **BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001**


<!-- SMART_DOC_GEN_TEST_DESCR - Start -->
(Smart Extension).  This test represents a typical Smart IS extension for representing MHE systems.  It takes the inventory that was created earlier by the  BASE_INV_CREATE_MOCA test (in a generated location).  It then calls a command to emulate the movement into the MHE system for the loads in that location.
<!-- SMART_DOC_GEN_TEST_DESCR - End -->

## **Test Category**

**☐** Custom

**🗹** Smart IS

**☐** Standard

## **Overview**

This initiative signifies a novel strategy wherein inventory is
systematically directed to designated Material Handling Equipment (MHE)
locations. It signifies a deliberate and focused effort to enhance
inventory management processes, ensuring precise allocation and optimal
utilization of resources within the system. The primary objective of
this approach is to enhance operational efficiency by strategically
assigning inventory to specific MHE locations, thereby promoting
streamlined handling procedures, and minimizing logistical bottlenecks.

By implementing this refined approach, the organization aims to achieve
greater efficiency in inventory management, leading to improved overall
operational performance. The strategy focuses on enhancing the accuracy
of inventory allocation, ensuring that resources are efficiently
utilized and minimizing the risk of stockouts or overstocking. This
strategic allocation of inventory to designated MHE locations is
expected to result in smoother handling processes, reducing the time and
effort required for material movement and enhancing the overall
efficiency of the supply chain.

## **Applicable versions**

This test is designed to support versions greater than **2008.x.x**,
ensuring compatibility and smooth operation with the latest software
releases. Users can confidently utilize this test, as it is optimized
for newer versions while retaining a user-friendly testing process.

## **Test Arguments**

Test arguments are parameters or inputs that are passed to the test
cases to customize the test execution. These arguments provide
flexibility and allow for the reuse of the same test case with different
sets of data or configurations. The input is as follows:


<!-- SMART_DOC_GEN_TEST_ARG - Start -->
<table>
<tr><th>Arguments</th><th>Argument Description</th></tr>
<tr><td>schbat</td><td>Wave# optionally</td></tr>
<tr><td>uc_call_complete_api</td><td>Determines if the API is called. Defaults to 1.</td></tr>
<tr><td>uc_dstlod</td><td>If provided, this is the load number where inventory is placed.</td></tr>
<tr><td>uc_dstlod_expr</td><td>If uc_dstlod is not passed, this expression is used to determine the load number. Default to 'ALD' || @uc_test_exec_seqnum || 'LL' || @uc_clean_lodnum</td></tr>
<tr><td>uc_emul_typ</td><td>Specifies the type of emulation. Defaults to PUT.</td></tr>
<tr><td>uc_max_load_cnt</td><td>Specifies the maximum count of loads that satisfy the srcloc and lodnum expression condition that will be moved. If not provided, all loads that satisfy the condition are moved.</td></tr>
<tr><td>uc_mhe_move_cmd</td><td>Command used to move inventory into MHE. Defaults to 'emulate user MHE process work queue'.</td></tr>
<tr><td>uc_mov_lodnum_expr</td><td>Loads matching this wildcard are moved.</td></tr>
<tr><td>uc_put_pending_dispatched_inv</td><td>Do we deposit pending deposit inventory? 1 or 0</td></tr>
<tr><td>uc_srcloc</td><td>Inventory is taken from this source location.</td></tr>
<tr><td>uc_test_exec_seqnum</td><td>During each run, it generates a unique base-36 value.</td></tr>
<tr><td>wh_id</td><td>This refers to the warehouse ID.</td></tr>
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

<!-- SMART_DOC_GEN_RUN_SET_USING_THIS - End -->

## **Equivalent Usecase**

The following steps represent a general procedure for putting inventory
into the MHE location through GUI.

Step:1

Select **Configuration** > **Inventory**

![](BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001/image1.png)
Step:2

Click on the **Inventory'** screen.

![](BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001/image2.png)


Step:3

Click on the **LPN'** screen.

![](BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001/image3.png)

Step:4

After that all LPNs are shown in it. You just need to select the LPN and
click Action and Move inventory, which you want to move the MHE
location.

![](BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001/image4.png)

Step:5

After putting required parameters, you just need to click on move.

![](BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001/image5.png)

## **Applicable MOCA commands**

Move inventory to MHE location using the MOCA command, you can use the
following command.

-   **UC MHE MOVE CMD**

This command will trigger the move inventory to MHE location based on
the predefined parameters and rules within the MOCA system.

## **Affected DB tables

When move inventory to MHE location, the following database tables are
typically affected:

-   **inventory_view**

-   **wrkque**

These tables are integral components of the inventory management system
and are essential for tracking and summarizing inventory data.

---

 **Previous-Test**
 [BASE_INB_0002100_TRLR_CKIN_MOCA_V001](./tests_docs/BASE_INB_0002100_TRLR_CKIN_MOCA_V001.md)
 
 **Next-Test**
  [BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001.md)

[SMART-IS](https://www.smart-is.pk) 