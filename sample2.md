<div>
  <h2>Overview</h2>
  <p style="font-size: large; text-align: left;">AuTest is an innovative automated testing solution that modernizes testing methods. It handles important tasks like managing tests, executing tests, and creating tests, making testing smoother and faster. AuTest is flexible and scalable, fitting perfectly into projects of any size.</p>
  <p><strong>Naming convention:</strong></p>
  <ul>
    <li>"INB", "INV" and "OUB" indicate the tests is related to inbound processes, inventory processes and outbound processes respectively.</li>
    <li>"0001100" and "0002100" are numeric identifiers representing process sequences.</li>
    <li>"COPY_TEMPLATE_RCVTRK" and "WAVE_PLAN" describe the specific functionality.</li>
    <li>"SMART" indicates that it is per typical Smart IS implementations.</li>
    <li>"MOCA", "WEB" and "RF" indicates that this is a MOCA-based test, WEB-based test and RF-based test respectively.</li>
    <li>"V001" signifies the version of the test.</li>
  </ul>
</div>

**MOCA**
| Tests | Descriptions |
|-----------|----------|
| [BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001.md) |Copy a template receive truck to a new one  |
| [BASE_INB_0002100_TRLR_CKIN_MOCA_V001](./tests_docs/BASE_INB_0002100_TRLR_CKIN_MOCA_V001.md) |Check in receive truck to an empty door  |
| [BASE_INB_0003100_IDENTIFY_MOCA_V001](./tests_docs/BASE_INB_0003100_IDENTIFY_MOCA_V001.md) |Identify inventory on the truck  |
| [BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001](./tests_docs/BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001.md) |Allocate location, pick up, deposit  |
| [BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001](./tests_docs/BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001.md) |(Smart Extension).  This test represents a typical Smart IS extension for representing MHE systems.  It takes the inventory that was created earlier by the  BASE_INV_CREATE_MOCA test (in a generated location).  It then calls a command to emulate the movement into the MHE system for the loads in that location.  |
| [BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001.md) |Close and dispatch receive trailer  |
| [BASE_INV_CREATE_MOCA_V001](./tests_docs/BASE_INV_CREATE_MOCA_V001.md) |Create multiple pallets in a location.  The destination location is created by copying a template location - this provides a way to seggregate inventory for each test run.  The inventory characteristics and pallet count are passed in.  |
| [BASE_INV_MOVE_MOCA_V001](./tests_docs/BASE_INV_MOVE_MOCA_V001.md) |This test will move the inventory we created earlier to a storage location.  |
| [BASE_OUB_0010000_ORD_COPY_TEMPLATE_MOCA_V001](./tests_docs/BASE_OUB_0010000_ORD_COPY_TEMPLATE_MOCA_V001.md) |This is the starting point of typical outbound tests.  It assumes that we have a template order.  It copies that order using the [copy order] command to a new order number.  The template order number can be a wild card, so it can create multiple orders.  All orders get the same value in wave_set column which allows us to later plan a single wave for these orders.  |
| [BASE_OUB_0010A00_ORD_SUBCONTR_MOCA_V001](./tests_docs/BASE_OUB_0010A00_ORD_SUBCONTR_MOCA_V001.md) |(Smart Extension).  This represents subcontracting process in a system like SAP.  It takes an order where we have a non-allocatable parent line that represents a finished good and its allocatable child lines represnet components.  This test first creartes a work order for producing the finished good using the component lines.  It then creates the order for finished good.  It then breaks them into two orders based on a Smart IS extension where we have a regular order with --WO suffix for consuming components and a regular order for the finished good.  |
| [BASE_OUB_0020000_WAVE_PLAN_MOCA_V001](./tests_docs/BASE_OUB_0020000_WAVE_PLAN_MOCA_V001.md) |The BASE tests that create orders, set ord.wave_set column.  This test builds upon that and plans a wave for the wave set.  So this allows for a mechanism to combine multiple orders into a single wave.  |
| [BASE_OUB_0030000_WAVE_ALLOC_MOCA_V001](./tests_docs/BASE_OUB_0030000_WAVE_ALLOC_MOCA_V001.md) |The BASE tests provide a way to plan multiple orders to a single wave.  It builds upon the same concepts to now allocate that wave.  So the whole framwework thus allows at this time to allocate multiple orders that were created earlier and planned to a single wave.  |
| [BASE_OUB_0040000_WAIT_REL_MOCA_V001](./tests_docs/BASE_OUB_0040000_WAIT_REL_MOCA_V001.md) |This test builds upon the concepts of other BASE outbound tests.  It will wait for the allocated wave to become completely released - so the core idea is that it is waiting for the pick release manager to do its job.  |
| [BASE_OUB_0050000_LIST_PICK_MOCA_V001](./tests_docs/BASE_OUB_0050000_LIST_PICK_MOCA_V001.md) |This tests builds upon other BASE outboudn tests.  It would do list picking for those orders using standard MOCA Commands.  |
| [BASE_OUB_0050A00_MHE_SMART_PICK_MOCA_V001](./tests_docs/BASE_OUB_0050A00_MHE_SMART_PICK_MOCA_V001.md) |(Smart Extension).  This test represents the typical MHE picking flow implemented by Smart IS.  In this model wrkque entries were created for each pick (carton or list).  The test will pick the list or carton fully.  |
| [BASE_OUB_0060000_PICK_HOP_MOCA_V001](./tests_docs/BASE_OUB_0060000_PICK_HOP_MOCA_V001.md) |This test builds on other BASE outbound tests.  Once inventory has been picked, it will move the picked loads through all the open hops using standard MOCA commands.  |
| [BASE_OUB_0070A00_VAS_SMART_PREP_MOCA_V001](./tests_docs/BASE_OUB_0070A00_VAS_SMART_PREP_MOCA_V001.md) |(Smart Extension).  This tests a typical Smart IS flow for VAS.  The picked inventory is brought to a workstation where some services are performed.  These services are termed [prep] services for a later VAS operation.  The test performs those actions and consumes the services.  |
| [BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001](./tests_docs/BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001.md) |(Smart Extension). This tests a typical Smart IS implementatin of pallet build.  Here picked inventory is brought to a workstation where user combines picked inventory to pallets.  |
| [BASE_OUB_0090000_STAGE_MOCA_V001](./tests_docs/BASE_OUB_0090000_STAGE_MOCA_V001.md) |This test will stage the shipments if not already staged  |
| [BASE_OUB_0200000_TRLR_CKIN_MOCA_V001](./tests_docs/BASE_OUB_0200000_TRLR_CKIN_MOCA_V001.md) |Check in shipping trailers  |
| [BASE_OUB_0250000_TRLR_LOAD_MOCA_V001](./tests_docs/BASE_OUB_0250000_TRLR_LOAD_MOCA_V001.md) |Load staged inventory to trailer  |
| [BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001](./tests_docs/BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001.md) |This test builds on other BASE outbound tests.  The test will wait for the outbound order to be completely dispatched.  |
| [BASE_OUB_0301000_TRLR_CLOSE_DISPATCH_MOCA_V001](./tests_docs/BASE_OUB_0301000_TRLR_CLOSE_DISPATCH_MOCA_V001.md) |Close and dispatch a shipping trailer  |



**WEB**
| Tests | Descriptions |
|-----------|----------|
| [BASE_OUB_0020100_WAVE_PLAN_WEB_V001](./tests_docs/BASE_OUB_0020100_WAVE_PLAN_WEB_V001.md) |Plan a wave using web screen  |
| [BASE_OUB_0030100_WAVE_ALLOC_WEB_V001](./tests_docs/BASE_OUB_0030100_WAVE_ALLOC_WEB_V001.md) |Allocate a wave using web screen  |
| [BASE_OUB_0035100_WAVE_REL_WEB_V001](./tests_docs/BASE_OUB_0035100_WAVE_REL_WEB_V001.md) |Release a wave using web screen  |



**RF**
| Tests | Descriptions |
|-----------|----------|
| [BASE_INV_0020100_MOVE_RF_V001](./tests_docs/BASE_INV_0020100_MOVE_RF_V001.md) |Move a load  |
| [BASE_OUB_0050100_LIST_PICK_RF_V001](./tests_docs/BASE_OUB_0050100_LIST_PICK_RF_V001.md) |This test will perform the differnt types of picks on RF  |