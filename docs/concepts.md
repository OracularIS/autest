## Overview

Smart AuTest is a comprehensive automated testing suite that requires no installation footprint. The metadata and results are stored in the cloud, where the security mechanism is tenant-based.

The test metadata primarily follows a low-code solution where tests are executed by abstractly representing the scenarios using data.

## About Test Data

Understanding how we should manage the test data is central to the whole project. Our vision is that customers can start using the solution immediately and require little day-to-day maintenance. We suggest the following paradigm to support this vision:

- Whenever a test is run, the framework always pushes a globally unique, base-36 string to the stack. This allows us to generate new data that is guaranteed to be unique. The name of this parameter is `uc_test_exec_seqnum`.

- For outbound tests, create some sample orders in the system with order lines and name them with specific conventions:
  - The `template_flg` for the orders will be set to 1.
  - Name them as `ATST-TMPL-<some identifier>`.

Stick to the conventions that we have for the template data – that will simplify using the tests we have provided.

## Type of Data

| Data Type                  | Description                                                                                  |
|----------------------------|----------------------------------------------------------------------------------------------|
| **Rules**                  |                                                                                              |
| **Source Orders to Copy**  | Named with prefix `ATST-TMPL-`. Set `template_flg` to 1                                       |
| **Test Orders Created**    | Named with prefix `ADATA-` and suffix of the test execution sequence number                   |
| **Wave Set**               | Orders created as part of one test run get the same value for `ord_line.wave_set`. This is `AW-` followed by the test execution sequence number |
| **Wave**                   | Waves created are named with prefix `ADATAW-` and suffix of the test execution sequence number|
| **Carrier Move – Host External Id** | For outbound tests starting with a carrier move, the host external id of the generated carrier move has the prefix `ADATA-` and the suffix is the test execution sequence number |
| **Receive Truck**          | New receive trucks are created with prefix `ARTRK-` and suffix of the test execution sequence number |
| **Receive Invoice**        | The receive invoice numbers are copied from the template data and the test execution sequence number is appended |
| **Receive PO Number**      | The receive PO numbers are copied from the template data and the test execution sequence number is appended |
| **Receipt ASN Data**       | For receiving tests, the ASN data (invlod, invsub, invdtl) for the source ASN is copied and the test execution sequence number is appended to identifiers like `lodnum`, `subnum`, `dtlnum`. The same applies to serial numbers and hold records. |

To support waving tests, the “some identifier” should be such that we can utilize wild card to plan waves such that shipments get a single shipment for multiple orders. For example, we can create `ATST-TMPL-X01` and `ATST-TMPL-X02` orders. Then run the test with source order number expression of `ATST-TMPL-X%`. This will create a single shipment for both.

