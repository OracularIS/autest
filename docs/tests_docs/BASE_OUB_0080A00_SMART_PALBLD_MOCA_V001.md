# **BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001**


<!-- SMART_DOC_GEN_TEST_DESCR - Start -->
(Smart Extension). This tests a typical Smart IS implementatin of pallet build.  Here picked inventory is brought to a workstation where user combines picked inventory to pallets.
<!-- SMART_DOC_GEN_TEST_DESCR - End -->

## **Test Category**

**☐** Custom  
**🗹** Smart IS  
**☐** Standard  

## **Overview**

In this innovative approach, the selection of inventory for shipment precedes the determination of whether pallet building is suitable for packing. This method involves first selecting items from the available inventory and subsequently assessing their compatibility for pallet packing. By prioritizing inventory selection over the determination of the packing method, this process optimizes the efficiency of the packing process.

By following this streamlined approach, the packing process becomes more efficient and adaptable to varying inventory requirements. This method ensures that the most suitable items are selected for shipment before determining the most appropriate packing method, thereby enhancing overall warehouse productivity and order fulfillment efficiency.

## **Applicable versions**

This test is designed to support versions greater than **2008.x.x**, ensuring compatibility and smooth operation with the latest software releases. Users can confidently utilize this test, as it is optimized for newer versions while retaining a user-friendly testing process.

## **Test Arguments**

Test arguments are parameters or inputs that are passed to the test cases to customize the test execution. These arguments provide flexibility and allow for the reuse of the same test case with different sets of data or configurations. The input is as follows:


<!-- SMART_DOC_GEN_TEST_ARG - Start -->
<table>
<tr><th>Arguments</th><th>Argument Description</th></tr>
<tr><td>ordnum</td><td>null</td></tr>
<tr><td>schbat</td><td>null</td></tr>
<tr><td>ship_id</td><td>null</td></tr>
<tr><td>uc_all_src_to_single_final</td><td>null</td></tr>
<tr><td>uc_do_direct_case_repack_when_allowed</td><td>null</td></tr>
<tr><td>uc_pb_arecod</td><td>null</td></tr>
<tr><td>uc_pb_ctncod</td><td>null</td></tr>
<tr><td>uc_pb_hgt</td><td>null</td></tr>
<tr><td>uc_pb_len</td><td>null</td></tr>
<tr><td>uc_pb_uc_hand_cond</td><td>null</td></tr>
<tr><td>uc_pb_uc_lodtyp</td><td>null</td></tr>
<tr><td>uc_pb_weight</td><td>null</td></tr>
<tr><td>uc_pb_wid</td><td>null</td></tr>
<tr><td>uc_test_exec_seqnum</td><td>null</td></tr>
<tr><td>uc_wave_set_expr</td><td>null</td></tr>
<tr><td>wave_set</td><td>null</td></tr>
<tr><td>wh_id</td><td>null</td></tr>
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

The following steps represent a general procedure for Smart Pallet build through GUI.

**Step:1**

Select **Configuration** > **Outbound Planner**

![](BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001/image1.png)

**Step:2**

Click on the **'Wave and Pick'** screen. All waves that are **Planned** are shown here.

![](BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001/image2.png)

**Step:3**

We simply allocate the order. Picks are shown in **picks** after allocation.

![](BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001/image3.png)

**Step:4**

After release pick, Picks are shown in pick confirmation.

![](BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001/image4.png)

**Step:5**

After that we will go to pallet build screen.

![](BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001/image5.png)

## **Applicable MOCA commands**

For Smart pallet build using the MOCA command, you can use the following command.

-   **uc_emulate_pick_cmd**

This command will trigger the Smart pallet build based on the predefined parameters and rules within the MOCA system.

## **Affected DB tables**

When Smart pallet build is created, the following database table is typically affected:

-   **Pckwrk_view**

This table likely contains information related to the work or tasks associated with building the pallets, such as the items to be included, quantities, locations, and other relevant details.


[SMART-IS](https://www.smart-is.pk) 