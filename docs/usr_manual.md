**Overview:**

The initial stage in inventory allocation for outbound orders or shipments involves meticulously planning them into a wave. Prior to allocation, all orders must be seamlessly integrated into a wave structure. Facilitating this process is the Outbound Planner module, designed to streamline warehouse operations comprehensively.The test scenario outlined is focused on planning multiple orders that are part of a wave set, consolidating them into a singular wave for efficient management.
#### View-test
[BASE_OUB_0020000_WAVE_PLAN_MOCA_V001](./tests_docs/BASE_OUB_0020000_WAVE_PLAN_MOCA_V001.md)

---

**Overview:**

Wave allocation in Blue Yonder optimizes order processing, reduces operational costs, and enhances customer satisfaction. Streamline your warehouse operations with efficient wave grouping. Prioritize orders, improve workflow, and adapt to changing demands seamlessly.
#### View-test
[BASE_OUB_0030000_WAVE_ALLOC_MOCA_V001](./tests_docs/BASE_OUB_0030000_WAVE_ALLOC_MOCA_V001.md)

---

**Overview:** 

Unlock the efficiency of your warehouse with Blue Yonder's Wave Release feature. Seamlessly transition batches of orders for streamlined processing. Maximize picking efficiency and minimize travel time with automated pick task generation. Improve order fulfillment rates and customer satisfaction with controlled and systematic wave releases.
#### View-test
[BASE_OUB_0040000_WAIT_REL_MOCA_V001](./tests_docs/BASE_OUB_0040000_WAIT_REL_MOCA_V001.md)

---

**Overview:** 

List picking involves the process of fulfilling customer orders by selecting and collecting items from the warehouse based on a generated picking list. This list is dynamically created, considering factors such as inventory levels, order priorities, and optimal picking routes. The software aims to optimize the efficiency of the picking process by organizing items in a logical sequence, reducing travel time for warehouse personnel.
#### View-test
 [BASE_OUB_0050000_LIST_PICK_MOCA_V001](./tests_docs/BASE_OUB_0050000_LIST_PICK_MOCA_V001.md)

---

**Overview:** 

In this concept, picked inventory will be transported through a series of hops, representing different stages or locations in the warehouse or distribution center. Each hop signifies a step in the process where the inventory moves closer to its destination, such as from picking to packing or from one area of the warehouse to another. This approach streamlines the movement of inventory by breaking down the process into smaller, manageable steps, ensuring that inventory is efficiently transferred and processed at each hop.
#### View-test
 [BASE_OUB_0060000_PICK_HOP_MOCA_V001](./tests_docs/BASE_OUB_0060000_PICK_HOP_MOCA_V001.md)

---

 **Overview:** 

To implement this use case effectively, the system needs to have a robust mechanism for tracking and managing trailer statuses. It should be able to handle various scenarios, such as delays or errors in the closing and dispatch process, and provide visibility into the status of each trailer.
#### View-test
 [BASE_OUB_0301000_TRLR_CLOSE_DISPATCH_MOCA_V001](./tests_docs/BASE_OUB_0301000_TRLR_CLOSE_DISPATCH_MOCA_V001.md)

---

 **Overview:** 

In this innovative approach, Material Handling Equipment (MHE) is employed to efficiently execute order picking tasks within a specified wave, following the established standards of Smart IS implementations. By leveraging MHE capabilities, this method enhances order picking processes, ensuring accuracy and efficiency in warehouse operations. This approach integrates seamlessly with Smart IS systems, providing a reliable and standardized solution for order fulfillment within warehouse environments.
#### View-test
 [BASE_OUB_0050A00_MHE_SMART_PICK_MOCA_V001](./tests_docs/BASE_OUB_0050A00_MHE_SMART_PICK_MOCA_V001.md)

---

 **Overview:** 

This implementation builds on the foundation of Smart IS principles, ensuring that the MHE-based order selection process seamlessly integrates with existing warehouse management systems. By following the typical Smart IS approach, the new concept aims to maintain compatibility and consistency with established practices, ensuring a smooth transition to the enhanced order picking process using MHE.
#### View-test
 [BASE_OUB_0070A00_VAS_SMART_PREP_MOCA_V001](./tests_docs/BASE_OUB_0070A00_VAS_SMART_PREP_MOCA_V001.md)

---

 **Overview:** 

In this innovative approach, the selection of inventory for shipment precedes the determination of whether pallet building is suitable for packing. This method involves first selecting items from the available inventory and subsequently assessing their compatibility for pallet packing. By prioritizing inventory selection over the determination of the packing method, this process optimizes the efficiency of the packing process.
#### View-test
 [BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001](./tests_docs/BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001.md)

---

 **Overview:** 

In the described use case, the system is designed to wait for an order to be dispatched, indicating a process that involves monitoring the status of an order until it reaches the "dispatched" state. This likely involves a system that tracks orders and their statuses, possibly interfacing with other systems or components that handle the actual dispatching process.
#### View-test
 [BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001](./tests_docs/BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001.md)

---

 **Overview:** 

Copying an existing order within a system involves duplicating an established order's details to streamline the process of creating a similar transaction. This functionality is beneficial when dealing with recurrent or similar orders, saving time, and ensuring consistency. To initiate this action, the user typically needs to identify the existing order they want to replicate.
#### View-test
 [BASE_OUB_0010000_ORD_COPY_TEMPLATE_MOCA_V001](./tests_docs/BASE_OUB_0010000_ORD_COPY_TEMPLATE_MOCA_V001.md)

---

 **Overview:** 

This represents subcontracting process in a system like SAP. It takes an order where we have a non-allocatable parent line that represents a finished good and its allocatable child lines represnet components. This test first creartes a work order for producing the finished good using the component lines. It then creates the order for finished good.
#### View-test
 [BASE_OUB_0010A00_ORD_SUBCONTR_MOCA_V001](./tests_docs/BASE_OUB_0010A00_ORD_SUBCONTR_MOCA_V001.md)

---

 **Overview:** 

Create multiple pallets in a location. The destination location is created by copying a template location - this provides a way to seggregate inventory for each test run. The inventory characteristics and pallet count are passed in.
#### View-test
 [BASE_INV_CREATE_MOCA_V001](./tests_docs/BASE_INV_CREATE_MOCA_V001.md)

---

 **Overview:** 

Inventory move is a fundamental operation where inventory is transferred from one specific location to another within the supply chain. This process could involve moving goods between different warehouses, distribution centers, or even within the same facility to optimize storage and accessibility. 
#### View-test
 [BASE_INV_MOVE_MOCA_V001](./tests_docs/BASE_INV_MOVE_MOCA_V001.md)

---

 **Overview:** 

Moving a load from one location to another within a warehouse is a critical task in logistics management. This operation involves safely transporting the load while ensuring minimal disruption to warehouse operations.  
#### View-test
[BASE_INV_0020100_MOVE_RF_V001](./tests_docs/BASE_INV_0020100_MOVE_RF_V001.md)

---

**Overview:** 

List picking involves the process of fulfilling customer orders by selecting and collecting items from the warehouse based on a generated picking list. This list is dynamically created, considering factors such as inventory levels, order priorities, and optimal picking routes. The software aims to optimize the efficiency of the picking process by organizing items in a logical sequence, reducing travel time for warehouse personnel.
#### View-test
 [BASE_OUB_0050100_LIST_PICK_RF_V001](./tests_docs/BASE_OUB_0050100_LIST_PICK_RF_V001.md)

---

 **Overview:** 

Copying an existing inbound order within a system involves duplicating an established order's details to streamline the process of creating a similar transaction. This functionality is beneficial when dealing with recurrent or similar orders, saving time, and ensuring consistency.
#### View-test
 [BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001.md)

---

 **Overview:** 

In the described use case, the system is designed to manage the process of checking in transport equipment to empty door, indicating a procedure that involves registering the arrival of transport vehicles or equipment at a designated location, such as a warehouse or distribution center. 
#### View-test
 [BASE_INB_0002100_TRLR_CKIN_MOCA_V001](./tests_docs/BASE_INB_0002100_TRLR_CKIN_MOCA_V001.md)

---

 **Overview:** 

This test represents a typical Smart IS extension for representing MHE systems. It takes the inventory that was created earlier by the BASE_INV_CREATE_MOCA test (in a generated location). It then calls a command to emulate the movement into the MHE system for the loads in that location.
#### View-test
 [BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001](./tests_docs/BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001.md)

---

 **Overview:** 

In the described use case, the system is designed to manage the process of closing and dispatching a received truck, indicating a procedure that involves finalizing the receipt of goods from a truck and preparing it for dispatch to its next destination.
#### View-test
 [BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001.md)

---

 **Overview:** 

The initial stage in inventory allocation for outbound orders or shipments involves meticulously planning them into a wave. Prior to allocation, all orders must be seamlessly integrated into a wave structure. Facilitating this process is the Outbound Planner module, designed to streamline warehouse operations comprehensively.
#### View-test
 [BASE_OUB_0020100_WAVE_PLAN_WEB_V001](./tests_docs/BASE_OUB_0020100_WAVE_PLAN_WEB_V001.md)

---

 **Overview:** 

Wave allocation is a strategic process that involves grouping orders together to streamline handling and improve operational efficiency. By consolidating orders into waves, businesses can better manage their inventory, optimize warehouse space, and reduce operational costs. 
#### View-test
 [BASE_OUB_0030100_WAVE_ALLOC_WEB_V001](./tests_docs/BASE_OUB_0030100_WAVE_ALLOC_WEB_V001.md)

---

 **Overview:** 

The initial stage in inventory allocation for outbound orders or shipments involves meticulously planning them into a wave. Prior to allocation, all orders must be seamlessly integrated into a wave structure. Facilitating this process is the Outbound Planner module, designed to streamline warehouse operations comprehensively.
#### View-test
 [BASE_OUB_0035100_WAVE_REL_WEB_V001](./tests_docs/BASE_OUB_0035100_WAVE_REL_WEB_V001.md)

---
