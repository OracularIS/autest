


#  **BASE_OUB_WAVE_PLAN_MOCA_V001**
## **Test Category**

**☐** Custom

**☐** Smart IS

**🗹** Standard

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

 
  
  | Parameter          | Description                                                                                        |
|--------------------|----------------------------------------------------------------------------------------------------|
| **uc_test_exec_seqnum**| During each run, it generates a unique base-36 value.                                               |
| **uc_wave_rule_nam**  | What wave rule are we going to use? For Alcon, the default is PUWH1 -- but our test itself cannot have a default.|
| **uc_wave_set_expr**   | If no wave set is provided, we default to creating one with the expression 'AW' join with @uc_test_exec_seqnum. |
| **wave_set**           | If not provided, we use our default value.                                                         |
| **uc_schbat_expr**     | If a specific scheduling batch is not given, we default it to 'ADATAW-' join with @uc_test_exec_seqnum.  |
| **schbat**             | What scheduling batch should we create? If not specified, we use uc_schbat_expr to determine it. |
| **Wh_id**              | If not specified, we use the first order from the wave set.                                         |
| **Client_id**          | If not specified, we use the client_id from the first order in the wave set.

**Equivalent Usecase**

The following steps represent a general procedure for planned wave
through GUI.

**Step:1**

Select **Configuration** \> **Outbound Planner**

![](mediaa/media/image1.png)

**Step:2**

Click on the **\'Wave and Pick\'** screen.

![](mediaa/media/image2.png)

**Step:3**

From the **Actions **drop-down list, select **Plan Wave.**

![](mediaa/media/image3.png)

**Step:4**

Under **Search Criteria**, from the **Rule Name** drop-down list, select
the rule that defines the parameters by which to search for orders or
shipments. Click **Search**. The orders or shipments that meet the
search criteria are displayed.

![](mediaa/media/image4.png)}

**Step:5**

Click **Plan Wave.**

![](mediaa/media/image5.png)

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

