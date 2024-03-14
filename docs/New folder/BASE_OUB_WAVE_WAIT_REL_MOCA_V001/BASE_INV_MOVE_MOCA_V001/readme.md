## **BASE_INV_MOV_MOCA_V001**

## **Test Category**
**☐** Custom

**☐** Smart IS

**🗹** Standard

## **Overview**

Inventory move is a fundamental operation where inventory is transferred
from one specific location to another within the supply chain. This
process could involve moving goods between different warehouses,
distribution centers, or even within the same facility to optimize
storage and accessibility. Blue Yonder provides tools and features to
facilitate this movement seamlessly, allowing users to initiate and
track the transfer of inventory with precision. By specifying the source
and destination locations, users can manage the logistics of the move
efficiently. The platform\'s real-time visibility and data analytics
ensure that businesses can make informed decisions during the inventory
move process, contributing to better overall supply chain management and
operational efficiency.

## **Applicable versions**

This test is designed to support versions greater than **2008.x.x**,
ensuring compatibility and smooth operation with the latest software
releases. Users can confidently utilize this test, as it is optimized
for newer versions while retaining a user-friendly testing process.

## **Test Arguments**

Test arguments are parameters or inputs that are passed to the test
cases to customize the test execution. These arguments provide
flexibility and allow for the reuse of the same test case with
different sets of data or configurations. The input is as follows:

| Parameter              | Description                                                                                           |
| ---------------------- | ----------------------------------------------------------------------------------------------------- |
| **uc_test_exec_seqnum**| During each run, it generates unique base-36 value.                                                   |
| **Wh_id**               | Choose the warehouse where you want to perform actions.                                               |
| **Uc_dstloc**           | Specify where you want to move inventory from source location.                                        |
| **Uc_srcloc**           | Optionally, indicate where you are taking inventory from.                                             |
| **Uc_mov_lodnum_expr**  | It provides a pattern for load numbers to move.                                                      |
| **Uc_srcloc_expr**      | If source location is not provided, this expression helps determine it. By default, it is 'ADSTLOC-' \| \| \@uc_test_exec_seqnum. |
| **Uc_dstloc_expr**      | If destination location is not provided, this expression helps determine it. By default, it's 'AMOVLOC-' \| \| \@uc_test_exec_seqnum. |
| **uc_max_load_cnt**     | Specify the maximum number of loads to move based on the source location and load number expression conditions. If not provided, all loads meeting the condition will be moved. |


## **Equivalent Usecase**

The following steps represent a general procedure for Move Inventory
through GUI.

**Step:1**

 Select **Configuration**  **Inventory**

![A screenshot of a computer Description automatically
generated](media_folder/media/image1.png)

**Step:2**
Click on the **Inventory** screen.

![](media_folder/media/image2.png)

**Step:3**
Click on **LPN** tab.

![A screenshot of a computer Description automatically
generated](media_folder/media/image3.png)

**Step:4**

Select the **specific LPN** you want to move. LPN will be shown in the
column.

![](media_folder/media/image4.png)

**Step:5**

Go to the **Actions** tab and click on **Move Inventory**

![](media_folder/media/image5.png)
**Note**: from the onsite tab, you can also select locations, and
click on a location and select LPN to view the LPN in the location.

![A screenshot of a computer Description automatically
generated](media_folder/media/image6.png)

**Step:6**

Confirm your choice by clicking **move** to move inventory from one
location to another.

## **Applicable MOCA commands**

To move a LPN using the MOCA command, you can use the following
command.

- **Move_inventory**

 This command will trigger the inventory move command based on the
 predefined parameters and rules within the MOCA system.


## **Affected DB Tables**

 When move inventory action perform, the following database tables are
 typically affected:

-   **Invlod**

-   **Invsub**

-   **Invdtl**

-   **invsum**

 These tables are crucial for tracking inventory movement and within
 the warehouse management system.



[SMART-IS](https://www.smart-is.pk) 

[Previous-Test](/DOCS/BASE_INV_CREATE_MOCA_V001/readme.md) - [Next-Test](/DOCS/BASE_OUB_LIST_PICK_MOCA_V001/readme.md)


