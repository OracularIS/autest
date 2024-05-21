<!-- docs/_sidebar.md --> 
- [Home](./readme.md)
- [Architecture Overview](./arch_overview.md)
- [Why Use AuTest?](./Why_AuTest.md)
- [AB2_Tests1](./sample2.md)
<details>
  <summary><strong>MOCA</strong></summary>
  
  - [BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001.md)
  - [BASE_INB_0002100_TRLR_CKIN_MOCA_V001](./tests_docs/BASE_INB_0002100_TRLR_CKIN_MOCA_V001.md)
  - [BASE_INB_0003100_IDENTIFY_MOCA_V001](./tests_docs/BASE_INB_0003100_IDENTIFY_MOCA_V001.md)
  - [BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001](./tests_docs/BASE_INB_0004100_ALLOCATE_LOCATION_PICKUP_DEPOSIT_MOCA_V001.md)
  - [BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001](./tests_docs/BASE_INB_0004A00_MHE_SMART_PUT_MOCA_V001.md)
  - [BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001](./tests_docs/BASE_INB_0009100_CLOSE_DISPATCH_RCVTRK_MOCA_V001.md)
</details>

<details>
  <summary><strong>WEB</strong></summary>
  
  - [BASE_OUB_0020100_WAVE_PLAN_WEB_V001](./tests_docs/BASE_OUB_0020100_WAVE_PLAN_WEB_V001.md)
  - [BASE_OUB_0030100_WAVE_ALLOC_WEB_V001](./tests_docs/BASE_OUB_0030100_WAVE_ALLOC_WEB_V001.md)
  - [BASE_OUB_0035100_WAVE_REL_WEB_V001](./tests_docs/BASE_OUB_0035100_WAVE_REL_WEB_V001.md)
</details>

<details>
  <summary><strong>RF</strong></summary>
  
  - [BASE_INV_0020100_MOVE_RF_V001](./tests_docs/BASE_INV_0020100_MOVE_RF_V001.md)
  - [BASE_OUB_0050100_LIST_PICK_RF_V001](./tests_docs/BASE_OUB_0050100_LIST_PICK_RF_V001.md)
</details>

<script>
  // Toggle visibility of nested lists when the summary is clicked
  document.addEventListener('DOMContentLoaded', function() {
    const details = document.querySelectorAll('details');
    details.forEach(detail => {
      detail.addEventListener('toggle', function() {
        if (detail.open) {
          // Close other open details elements
          details.forEach(otherDetail => {
            if (otherDetail !== detail && otherDetail.open) {
              otherDetail.open = false;
            }
          });
        }
      });
    });
  });
</script>
