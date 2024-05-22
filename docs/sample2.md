# Overview

AuTest is an innovative automated testing solution that modernizes testing methods. It handles important tasks like managing tests, executing tests, and creating tests, making testing smoother and faster. AuTest is flexible and scalable, fitting perfectly into projects of any size.

**Naming convention:**

- "INB", "INV" and "OUB" indicate the tests related to inbound processes, inventory processes, and outbound processes respectively.
- "0001100" and "0002100" are numeric identifiers representing process sequences.
- "COPY_TEMPLATE_RCVTRK" and "WAVE_PLAN" describe the specific functionality.
- "SMART" indicates that it is per typical Smart IS implementations.
- "MOCA", "WEB", and "RF" indicate that this is a MOCA-based test, WEB-based test, and RF-based test respectively.
- "V001" signifies the version of the test.

<script>
    // JavaScript function to handle sidebar link clicks
    document.addEventListener("DOMContentLoaded", function () {
        var sidebarLinks = document.querySelectorAll('.sidebar-link');

        sidebarLinks.forEach(function (link) {
            link.addEventListener('click', function (event) {
                // Prevent default link behavior
                event.preventDefault();

                // Remove active class from all sidebar links
                sidebarLinks.forEach(function (item) {
                    item.classList.remove('active');
                });

                // Add active class to the clicked sidebar link
                this.classList.add('active');

                // Get the test ID from the data attribute
                var testId = this.getAttribute('data-test-id');

                // Expand the corresponding sidebar section
                var section = document.querySelector('.sidebar-section[data-test-id="' + testId + '"]');
                if (section) {
                    section.classList.add('active');
                }
            });
        });
    });
</script>

**MOCA**

| Tests | Descriptions |
|-------|--------------|
| [BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001.md){: class="sidebar-link" data-test-id="BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001"} |Copy a template receive truck to a new one  |
| [BASE_INB_0002100_TRLR_CKIN_MOCA_V001](./tests_docs/BASE_INB_0002100_TRLR_CKIN_MOCA_V001.md){: class="sidebar-link" data-test-id="BASE_INB_0002100_TRLR_CKIN_MOCA_V001"} |Check in receive truck to an empty door  |
| [BASE_INB_0003100_IDENTIFY_MOCA_V001](./tests_docs/BASE_INB_0003100_IDENTIFY_MOCA_V001.md){: class="sidebar-link" data-test-id="BASE_INB_0003100_IDENTIFY_MOCA_V001"} |Identify inventory on the truck  |
| [BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001](./tests_docs/BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001.md){: class="sidebar-link" data-test-id="BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001"} |Allocate location, pick up, deposit  |
| [BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001](./tests_docs/BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001.md){: class="sidebar-link" data-test-id="BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001"} |(Smart Extension).  This test represents a typical Smart IS extension for representing MHE systems.  It takes the inventory that was created earlier by the  BASE_INV_CREATE_MOCA test (in a generated location).  It then calls a command to emulate the movement into the MHE system for the loads in that location.  |
| [BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001.md){: class="sidebar-link" data-test-id="BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001"} |Close and dispatch receive trailer  |
| [BASE_INV_CREATE_MOCA_V001](./tests_docs/BASE_INV_CREATE_MOCA_V001.md){: class="sidebar-link" data-test-id="BASE_INV_CREATE_MOCA_V001"} |Create multiple pallets in a location.  The destination location is created by copying a template location - this provides a way to seggregate inventory for each test run.  The inventory characteristics and pallet count are passed in.  |
| [BASE_INV_MOVE_MOCA_V001](./tests_docs/BASE_INV_MOVE_MOCA_V001.md){: class="sidebar-link" data-test-id="BASE_INV_MOVE_MOCA_V001"} |This test will move the inventory we created earlier to a storage location.  |
| [BASE_OUB_0010000_ORD_COPY_TEMPLATE_MOCA_V001](./tests_docs/BASE_OUB_0010000_ORD_COPY_TEMPLATE_MOCA_V001.md){: class="sidebar-link" data-test-id="BASE_OUB_0010000_ORD_COPY_TEMPLATE_MOCA_V001"} |This is the starting point of typical outbound tests.  It assumes that we have a template order.  It copies that order using the [copy order] command to a new order number.  The template order number can be a wild card, so it can create multiple orders.  All orders get the same value in wave_set column which allows us to later plan a single wave for these orders.  |
| [BASE_OUB_0010A00_ORD_SUBCONTR_MOCA_V001](./tests_docs/BASE_OUB_0010A00_ORD_SUBCONTR_MOCA_V001.md){: class="sidebar-link" data-test-id="BASE_OUB_0010A00_ORD_SUBCONTR_MOCA_V001"} |(Smart Extension).  This represents subcontracting process in a system like SAP.  It takes an order where we have a non-allocatable parent line that represents a finished good and its allocatable child lines represnet components.  This test first creartes a work order for producing the finished good using the component lines.  It then creates the order for finished good.  It then breaks them into two orders based on a Smart IS extension where we have a regular order with --WO suffix for consuming components and a regular order for the finished good.  |
| [BASE_OUB_0020000_WAVE_PLAN_MOCA_V001](./tests_docs/BASE_OUB_0020000_WAVE_PLAN_MOCA_V001.md){: class="sidebar-link" data-test-id="BASE_OUB_0020000_WAVE_PLAN_MOCA_V001"} |The BASE tests that create orders, set ord.wave_set column.  This test builds upon that and plans a wave for the wave set.  So this allows for a mechanism to combine multiple orders into a single wave.  |
| [BASE_OUB_0030000_WAVE_ALLOC
