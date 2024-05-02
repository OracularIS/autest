# **BASE_OUB_0090000_STAGE_MOCA_V001**


<!-- SMART_DOC_GEN_TEST_DESCR - Start -->
This test will stage the shipments if not already staged
<!-- SMART_DOC_GEN_TEST_DESCR - End -->

## **Test Category**

<input type="checkbox" checked disabled> Standard
<br>
<input type="checkbox" disabled> Custom
<br>
<input type="checkbox" disabled> Smart IS


## **Overview**

The process of staging shipments is a critical step in ensuring the timely and accurate delivery of goods to customers. A key requirement in this process is that a shipment must be fully picked and in a staging lane before it can be staged. This prerequisite serves as a crucial quality control measure, ensuring that all items in a shipment have been accurately picked and verified before being staged for loading onto delivery vehicles. By enforcing this requirement, warehouse managers can significantly reduce the risk of errors, such as missing items or incorrect quantities, which can lead to delays and customer dissatisfaction.

This requirement also helps streamline the staging process by ensuring that all necessary items for a shipment are consolidated in a single location, ready for efficient loading onto trucks or other transport vehicles. By having shipments fully picked and staged in advance, warehouse staff can minimize the time and effort required to prepare shipments for delivery, ultimately improving overall operational efficiency. Additionally, this practice helps maintain a smooth flow of goods through the warehouse, enabling more efficient use of resources and reducing the likelihood of congestion or bottlenecks in the staging area.

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
<tr><td>client_id</td><td></td></tr>
<tr><td>uc_new_ordnum_expr</td><td></td></tr>
<tr><td>uc_new_wave_set_expr</td><td></td></tr>
<tr><td>uc_set_wave_set</td><td></td></tr>
<tr><td>uc_src_ordnum_expr</td><td></td></tr>
<tr><td>uc_test_exec_seqnum</td><td></td></tr>
<tr><td>wh_id</td><td></td></tr>
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
| BASE_OUB_000000_CREATE_TO_DISPATCH | create order, plan, allocate, release, pick, dispatch |
| BASE_OUB_001000_TRAFFIC_PLAN_CREATE_TO_DISPATCH | create order, plan, allocate, release, pick, dispatch |

<!-- SMART_DOC_GEN_RUN_SET_USING_THIS - End -->

## **Equivalent Usecase**

The following steps represent a general procedure for stage shipment through GUI.

**Step:1**

Select **Configuration** > **Outbound Planner**

![](BASE_OUB_0090000_STAGE_MOCA_V001/image1.png)

**Step:2**

Click on the **'Wave and Pick'** screen.

![](BASE_OUB_0090000_STAGE_MOCA_V001/image2.png)

**Step:3**

From the **Actions** drop-down list, select **Plan Wave.**

![](BASE_OUB_0090000_STAGE_MOCA_V001/image3.png)

**Step:4**

Under **Search Criteria**, from the **Rule Name** drop-down list, select the rule that defines the parameters by which to search for orders or shipments. Click **Search**. The orders or shipments that meet the search criteria are displayed.

![](BASE_OUB_0090000_STAGE_MOCA_V001/image4.png)

**Step:5**

Click **Plan Wave.**

![](BASE_OUB_0090000_STAGE_MOCA_V001/image5.png)

**Step:6**

Open that Plan wave and go to the '**Actions**' tab and pick '**Allocate Wave (Planned)**'.

![](BASE_OUB_0090000_STAGE_MOCA_V001/image6.png)

**Note**: Picks in a specific LPN level are released whenever the check box for the LPN level is selected for immediate release or when all three LPN levels are deselected.

![](BASE_OUB_0090000_STAGE_MOCA_V001/image7.png)

**Step:7**

From the Actions drop-down list, select Stage Shipment. A confirmation message is displayed.

![](BASE_OUB_0090000_STAGE_MOCA_V001/image8.png)


## **Applicable MOCA commands**

To stage shipment using the MOCA command, you can use the following command.

- check ok to stage shipment
- write stage shipment


This command will trigger the stage shipment based on the predefined parameters and rules within the MOCA system.

## **Affected DB tables**

The following database table is typically affected while stage shipment:

- **Shipment**
- **Shipment_line**

These tables are likely to be affected to stage shipment.

---

**Previous-Test**
 [BASE_OUB_0035100_WAVE_REL_WEB_V001](./tests_docs/BASE_OUB_0035100_WAVE_REL_WEB_V001.md)
 
**Next-Test**
  [BASE_OUB_0250000_TRLR_LOAD_MOCA_V001](./tests_docs/BASE_OUB_0250000_TRLR_LOAD_MOCA_V001.md)
  
[SMART-IS](https://www.smart-is.pk) 