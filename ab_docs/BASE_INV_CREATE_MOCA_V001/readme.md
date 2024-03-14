
## **BASE_INV_CREATE_MOCA_V001**

## **Test Category**
**☐** Custom

**☐** Smart IS

**🗹** Standard

## **Overview**

The Inventory Create feature allows users to input a variety of items
and their corresponding attributes with precision. This includes details
such as product descriptions, materials, quantities, and specific
storage locations. By doing so, users can maintain accurate and
up-to-date records of their inventory. Additionally, this functionality
enables users to efficiently create multiple pallets within specified
locations, streamlining the overall inventory management process.

Users can leverage the Inventory Create feature to input diverse items
and their associated attributes accurately. This includes specifying
details such as product descriptions, materials, quantities, and
specific storage locations. By doing so, users can ensure the
maintenance of precise and current inventory records. Furthermore, this
functionality empowers users to effortlessly generate multiple pallets
within designated locations, thereby enhancing the efficiency of their
inventory management processes.

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

| Parameter              | Description                                                                                           |
| ---------------------- | ----------------------------------------------------------------------------------------------------- |
| **uc_test_exec_seqnum** | During each run, uc_test_exec_seqnum generates unique base-36 value.                                 |
| **Wh_id**               | This is the warehouse ID where the inventory will be created.                                         |
| **Prt_client_id**      | This is the client ID for the part. It defaults to a specific value if not provided.                 |
| **Prtnum**             | This specifies the part for which inventory is being created.                                         |
| **Uc_dstloc**          | This is the location where the inventory will be created.                                             |
| **uc_template_dstloc** | If no destination location is provided, this location is copied to create a new storage location.   |
| **uc_dstloc_expr**     | If no destination location is provided, this expression is used to generate one.                     |
|                        | The default expression is 'ADSTLOC-\' \| \| \@uc_test_exec_seqnum                                   |
| **Palcnt**             | This is the number of loads to create.                                                                |
| **uc_lodnum_prefix**   | This is the prefix for newly created loads. If provided, the loads are created with this prefix      |
|                        | followed by the sequence number. If not provided, the loads are created with the next available     |
|                        | load number.                                                                                          |
| **new_untqty**         | This specifies the quantity of the newly created inventory. If not provided, it defaults to the     |
|                        | unit quantity per pallet.                                                                            |
| **Ftpcod**             | This specifies the footprint to use. If not provided, the footprint returned by prtftp for the part  |
|                        | is used.                                                                                              |
| **Lotnum**             | This specifies the lot to use. If not provided, the lot with the latest expiration date is used.    |
| **inv_attr_str1,       | These are inventory attribute strings.                                                               |
| inv_attr_str2,         |                                                                                                       |
| inv_attr_str3,         |                                                                                                       |
| inv_attr_str4,         |                                                                                                       |
| inv_attr_str5**        |                                                                                                       |
| **Revlvl, Orgcod,     | If not provided, the receive status from prtmst is used.                                              |
| Invsts**               |                                                                                                       |


## **Equivalent Usecase**

The following steps represent a general procedure for creating inventory
through GUI.

**Step:1**

Select **Configuration** > **Inventory**

![](media_folder/media/image1.png)

**Step:2**

Click on the **Inventory** screen.

![](media_folder/media/image2.png)

**Step:3**

After that you must select the specific location in which you want to
create inventory. After selecting inventory go to **Action** and **Add
Inventory**.

![](media_folder/media/image3.png)

**Step:4**

You must put required arguments in this step.

![](media_folder/media/image4.png)

**Step:5**

After putting arguments, you just need to click on Next and your
required inventory will add on this location.

## **Applicable MOCA commands**

To create the inventory using the MOCA command, you can use the
following command.

-   **Create inventory**

This command will trigger the inventory creation based on the predefined
parameters and rules within the MOCA system.

## **Affected DB Tables**

When creating the inventory, the following database tables are
typically affected:

-   **inventory_view**

-   **locmst**

-   **prtmst_view**

These tables are integral components of the inventory management system
and are essential for tracking and summarizing inventory data.


[SMART-IS](https://www.smart-is.pk) 

[Previous-Test](/DOCS/BASE_OUB_WAVE_WAIT_REL_MOCA_V001/readme.md) - [Next-Test](/DOCS/BASE_INV_MOVE_MOCA_V001/readme.md)