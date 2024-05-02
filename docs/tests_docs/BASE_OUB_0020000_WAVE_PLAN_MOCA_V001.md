# **BASE_OUB_0020000_WAVE_PLAN_MOCA_V001**


<!-- SMART_DOC_GEN_TEST_DESCR - Start -->
<!-- SMART_DOC_GEN_TEST_DESCR - End -->

## **Test Category**

<input type="checkbox" checked disabled> Standard
<br>
<input type="checkbox" disabled> Custom
<br>
<input type="checkbox" disabled> Smart IS


## **Overview**
The initial stage in inventory allocation for outbound orders or
shipments involves meticulously planning them into a wave. Prior to
allocation, all orders must be seamlessly integrated into a wave
structure. Facilitating this process is the Outbound Planner module,
designed to streamline warehouse operations comprehensively.

This module enables users to effectively adjust inventory, process
orders, manage shipments, and perform various other essential functions.
It serves as a pivotal tool in enhancing warehouse efficiency, ensuring
smooth operations, and ultimately boosting productivity.

The test scenario outlined is focused on planning multiple orders that
are part of a wave set, consolidating them into a singular wave for
efficient management.

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
<tr><td>client_id</td><td>If not specified, we use the client_id from the first order in the wave set.</td></tr>
<tr><td>schbat</td><td>What scheduling batch should we create? If not specified, we use uc_schbat_expr to determine it.</td></tr>
<tr><td>uc_schbat_expr</td><td>If a specific scheduling batch is not given, we default it to ‘ADATAW-‘ || @uc_test_exec_seqnum</td></tr>
<tr><td>uc_test_exec_seqnum</td><td>During each run, it generates unique base-36 value.</td></tr>
<tr><td>uc_wave_rule_nam</td><td>What wave rule are we going to use? For Alcon default is PUWH1 – but our test itself cannot have a default</td></tr>
<tr><td>uc_wave_set_expr</td><td>If no wave set is provided, we default to creating one with the expression ‘AW’ || @uc_test_exec_seqnum</td></tr>
<tr><td>wave_set</td><td>If not provided, we use our default value.</td></tr>
<tr><td>wh_id</td><td>If not specified, we use the first order from the wave set.</td></tr>
</table>
<!-- SMART_DOC_GEN_TEST_ARG - End -->

## **TestCases using this test**

This section provides a comprehensive list of test cases that are associated with this particular test. It provides a quick reference for understanding the specific tests covered. By reviewing these test cases, users can gain a deeper understanding of how this test is used in different scenarios and ensure comprehensive test coverage.


<!-- SMART_DOC_GEN_TEST_CASE_USING_THIS - Start -->
<!-- SMART_DOC_GEN_TEST_CASE_USING_THIS - End -->

## **RunSets using this test**

This section details the various RunSets that utilize this test as part of their execution. Each RunSet represents a collection of tests and configurations that are executed together to achieve specific testing goals. By examining the RunSets that include this test, users can understand how it fits into larger testing scenarios and how it contributes to overall test coverage and automation.


<!-- SMART_DOC_GEN_RUN_SET_USING_THIS - Start -->
<!-- SMART_DOC_GEN_RUN_SET_USING_THIS - End -->

## **Equivalent Usecase**

The following steps represent a general procedure for planned wave
through GUI.

**Step:1**

Select **Configuration** > **Outbound Planner**

![](BASE_OUB_0020000_WAVE_PLAN_MOCA_V001/image1.png)

**Step:2**

Click on the **\'Wave and Pick\'** screen.

![](BASE_OUB_0020000_WAVE_PLAN_MOCA_V001/image2.png)

**Step:3**

From the **Actions **drop-down list, select **Plan Wave.**

![](BASE_OUB_0020000_WAVE_PLAN_MOCA_V001/image3.png)

**Step:4**

Under **Search Criteria**, from the **Rule Name** drop-down list, select
the rule that defines the parameters by which to search for orders or
shipments. Click **Search**. The orders or shipments that meet the
search criteria are displayed.

![](BASE_OUB_0020000_WAVE_PLAN_MOCA_V001/image4.png)}

**Step:5**

Click **Plan Wave.**

![](BASE_OUB_0020000_WAVE_PLAN_MOCA_V001/image5.png)

## **Applicable MOCA commands**

To plan a wave using the MOCA command, you can use the following
command.

-  **process wave rules**

This command will trigger the plan wave based on the predefined
parameters and rules within the MOCA system.

## **Affected DB Tables**
When planning a wave, the following database table is typically
affected:

-   **Ord_line**

This table contains information about the planning waves for efficient
picking and processing in a warehouse environment.

---

**Next-Test**
[BASE_OUB_0030000_WAVE_ALLOC_MOCA_V001](./tests_docs/BASE_OUB_0030000_WAVE_ALLOC_MOCA_V001.md)
 
[SMART-IS](https://www.smart-is.pk) 