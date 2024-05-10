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



| Tests | Descriptions |
|-----------|----------|
|**MOCA**|
| [BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001.md) | Copying an existing inbound order within a system. |
| [BASE_INB_0002100_TRLR_CKIN_MOCA_V001](./tests_docs/BASE_INB_0002100_TRLR_CKIN_MOCA_V001.md) | Managing the process of checking in transport equipment to empty door. |
| [BASE_INB_0003100_IDENTIFY_MOCA_V001](./tests_docs/BASE_INB_0003100_IDENTIFY_MOCA_V001.md) | Identification process involves uniquely recognizing and tracking items, orders, or entities within the system. |
| [BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001](./tests_docs/BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001.md) | Optimizes inventory pickup and deposit by efficiently allocating locations based on various factors.|
| [BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001](./tests_docs/BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001.md) | Representing MHE systems in a Smart IS extension. |
| [BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001.md) | Managing the process of closing and dispatching a received truck. |
| [BASE_INV_CREATE_MOCA_V001](./tests_docs/BASE_INV_CREATE_MOCA_V001.md) | Creating multiple pallets in a location with specified characteristics. |
| [BASE_INV_MOVE_MOCA_V001](./tests_docs/BASE_INV_MOVE_MOCA_V001.md) | Transferring inventory from one location to another within the supply chain. |
| [BASE_OUB_0010000_ORD_COPY_TEMPLATE_MOCA_V001](./tests_docs/BASE_OUB_0010000_ORD_COPY_TEMPLATE_MOCA_V001.md) | Copying an existing order within a system to streamline creating similar transactions. |
| [BASE_OUB_0020000_WAVE_PLAN_MOCA_V001](./tests_docs/BASE_OUB_0020000_WAVE_PLAN_MOCA_V001.md) | Planning multiple orders into a wave for efficient management. |
| [BASE_OUB_0030000_WAVE_ALLOC_MOCA_V001](./tests_docs/BASE_OUB_0030000_WAVE_ALLOC_MOCA_V001.md) | Optimizing order processing, reducing costs, and enhancing customer satisfaction through wave allocation. |
| [BASE_OUB_0040000_WAIT_REL_MOCA_V001](./tests_docs/BASE_OUB_0040000_WAIT_REL_MOCA_V001.md) | Maximizing picking efficiency and minimizing travel time with automated pick task generation. |
| [BASE_OUB_0050000_LIST_PICK_MOCA_V001](./tests_docs/BASE_OUB_0050000_LIST_PICK_MOCA_V001.md) | Fulfilling customer orders by selecting and collecting items based on a picking list. |
| [BASE_OUB_0060000_PICK_HOP_MOCA_V001](./tests_docs/BASE_OUB_0060000_PICK_HOP_MOCA_V001.md) | Streamlining inventory movement through a series of hops in the warehouse. |
| [BASE_OUB_0090000_STAGE_MOCA_V001](./tests_docs/BASE_OUB_0090000_STAGE_MOCA_V001.md) | Ensuring shipments are fully picked and in a staging lane before staging. |
| [BASE_OUB_0200000_TRLR_CKIN_MOCA_V001](./tests_docs/BASE_OUB_0200000_TRLR_CKIN_MOCA_V001.md) | Managing the process of checking in transport equipment. |
| [BASE_OUB_0250000_TRLR_LOAD_MOCA_V001](./tests_docs/BASE_OUB_0250000_TRLR_LOAD_MOCA_V001.md) | Assigning staged shipments to stops in an outbound load for loading. |
| [BASE_OUB_0010A00_ORD_SUBCONTR_MOCA_V001](./tests_docs/BASE_OUB_0010A00_ORD_SUBCONTR_MOCA_V001.md) | Representing subcontracting process in a system like SAP. |
| [BASE_OUB_0050A00_MHE_SMART_PICK_MOCA_V001](./tests_docs/BASE_OUB_0050A00_MHE_SMART_PICK_MOCA_V001.md) | Enhancing order picking processes with Material Handling Equipment (MHE). |
| [BASE_OUB_0070A00_VAS_SMART_PREP_MOCA_V001](./tests_docs/BASE_OUB_0070A00_VAS_SMART_PREP_MOCA_V001.md) | Implementing MHE-based order selection process within warehouse management systems. |
| [BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001](./tests_docs/BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001.md) | Optimizing the efficiency of the packing process by selecting inventory before determining pallet building. |
| [BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001](./tests_docs/BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001.md) | Managing the process of waiting for an order to be dispatched. |


|**WEB**|
| [BASE_OUB_0020100_WAVE_PLAN_WEB_V001](./tests_docs/BASE_OUB_0020100_WAVE_PLAN_WEB_V001.md) | Planning orders into a wave for efficient management. |
| [BASE_OUB_0030100_WAVE_ALLOC_WEB_V001](./tests_docs/BASE_OUB_0030100_WAVE_ALLOC_WEB_V001.md) | Grouping orders together to streamline handling and improve operational efficiency. |


|**RF**|
| [BASE_INV_0020100_MOVE_RF_V001](./tests_docs/BASE_INV_0020100_MOVE_RF_V001.md) | Safely transporting loads within a warehouse to minimize disruption. |
