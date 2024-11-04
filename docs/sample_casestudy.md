## Introduction

This is a sample case study.  Going through the case study will allow us to visualize how an automated testing project may be approached:

### Inbound Tests

### Gather existing test scripts for inbound
It helps if we have manual test scripts that are already in use which will be migrated to the automated testing suite.  For illustration note that a typical manual test script may look something like:

| Step | Description | Expected Result |
|------|-------------|-----------------|
| 1000 |Prepare an ASN| ASN Exists in the system |
| 1100 |Create a trailer and check it in |<ul><li>Trailer Created </li>  <li> Workflows for the check in (e.g. temperature) were prompted </li> <li>Say yes to all workflows and type any temperation</li> </ul>  |
| 1200 |Assign trailer to the ASN | Trailer is assigned to the ASN |
| 1300 |Receive all loads on the ASN|All loads are received |
| 1400 |Choose a putaway method (e.g. directed on undirected) | Allowed to select it |
| 1500 |Put inventory into receive staging area| Inventory deposited |
| 1600 |Repeat 1300-1500 for all loads in ASN||
| 1700 |Scan load and deposit to final location| inventory moved to final location|
| 1800 |Repeat above for all loads | |
| 1900 |Close and dispatch the receive Truck|Receive Truck dispatched|
| 2000 |Validate inventory status|Inentory should be in Q status|
| 2100 |Move part of inventory to RF|Inventory moved to RF.  Make a note of the new load number|
| 2200 |Change status of this partial load to A|Make sure status of this is changed as we did/did not set transction to host|

#### Find equivaltent run set in the Smart AuTest suite
A specific manual test sequence may or may not exist exactly in the same way in our test suite.  As indicated in the concpts section, we have two core concepts:
- Test and test case
- Run Sets
Test cases are the building blocks that provide the core units of functionality.  So we already have test/test cases for the steps defined above.  Then they are brought together in the form of a run set.  Smart IS provides a rich set of test/test cases and also run sets.  While it is possible to easily create customer specific run sets, we encourage that the customers try to use the standard `BASE` run sets.

For this scenario, we have following run sets that will work:
| Run Set | Description |
|---------|-------------|
| BASE_INB_000000_CREATE_TO_DISPATCH | Perform the receiving end to end test using MOCA Commands |
| BASE_INB_000100_CREATE_TO_DISPATCH_USING_RF | Same steps as above but the inventory is handled via RF |
| BASE_INB_000200_CREATE_TO_DISPATCH_USING_RF_AND_WEB | Same as RF based run set, but use web for trailer check in |

We strongly encourage that for majority of scenarios, we employ MOCA based tests as they work much faster and call the same APIs - so that is the first run set.  Others are available as well, but if used to receive large master receipts, it will be slower.  This run set covers our steps 1000 - 1900 exactly.
 <img src="./images/smaple_casestudy/create_to_dispatch.jpg" alt="undirectedmenu" style= "margin:auto;display:block">
We then have the option to change status of everything (so slightly different from how step 2100 and 2200 handle it).  The manual test are testing two pieces of functionality with one test:
- That we can do partial inventory moe
- And then that we sent transaction properly

We have tests available for partial inventory move as well.  This is 
| Test | Description |
|------|-------------|
| BASE_INV_MOVE_MOCA_V002 | Move inventory to another location |
| BASE_INV_PARTIAL_MOVE_MOCA_V001 | Do partial inventory move.  We can give a quantity|

So we have following options:
- We could create a new run set which performs exactly what the manual test does.
- Or we could break up our tests into two.
    - We do a test for processing ASN all the way and change status
    - And then run a spearate run set which does every type of inventory move
     <img src="./images/smaple_casestudy/Runset_base_inv_ops.jpg" alt="undirectedmenu" style= "margin:auto;display:block">

By following this strategy we get an even wider test coverage.  But both options are available when adopting Smart IS test suite.

#### Same run set can test several scenarios
We may have differnt types of ASNs.  Or differnt types of items.  Our expected results may differ based on the type of data **but in many cases the test steps will not chnage**.  Smart autest suite lets you take advantage if this common tesing pattern.  We encourage using the same run set for multiple scenarios.  While we may be running the same exact run set, we can create differnt "test cases" for each "run set".  

### Outbound Tests

### Gather existing test scripts for inbound
It helps if we have manual test scripts that are already in use which will be migrated to the automated testing suite.  For illustration note that a typical manual test script may look something like:
| Step | Description | Expected Result |
|------|-------------|-----------------|
| 1000 |Prepare an order| Order Exists in the system.  _This is where we may be representing differnt scenarios like each picking, parcel etc_ |
| 1100 |Plan wave for the order| Wave has been planned|
| 1200 |Allocate the wave| Wave has been allocated|
| 1300 |Wait for wave to release| Wait until work is created|
| 1400 |Peform picking| Picks are complete|
| 1500 |Deposit| Picks are deposited to staging|
| 1500 |Dispatch the shipment| Shipment is dispatched|

#### Find equivaltent run set in the Smart AuTest suite
A specific manual test sequence may or may not exist exactly in the same way in our test suite.  As indicated in the concpts section, we have two core concepts:
- Test and test case
- Run Sets
Test cases are the building blocks that provide the core units of functionality.  So we already have test/test cases for the steps defined above.  Then they are brought together in the form of a run set.  Smart IS provides a rich set of test/test cases and also run sets.  While it is possible to easily create customer specific run sets, we encourage that the customers try to use the standard `BASE` run sets.

For this scenario, we have following run sets that will work:
| Run Set | Description |
|---------|-------------|
| BASE_OUB_000000_CREATE_TO_DISPATCH | Perform the receiving end to end test using MOCA Commands |
| BASE_OUB_000100_CREATE_TO_DISPATCH_USING_FRONT_END | Perform the receiving end to end test using MOCA Commands |

We encourage that customers use MOCA based tests as much as possible for stremlined testing.


### Directed Work
We have an independent elaborate run set that can perform any type of direcetd work:
| Run Set | Description |
|---------|-------------|
| BASE_WRK_000000_DO_ANY_WORK_MOCA | Do wny work from directed work|
| BASE_WRK_001000_DO_INTERLEAVE | Same as above, but lets you create a master receipt and order at the same time to see interleaving|

### Paperwork
Often the paperwork tests are done inline with the manual tests.  This is generally done as testing is laboroius and we want to do as many tests in one pass as possible.  This can sometime lead to missed issue.  For example a change in the MOCA comamnd for a certain report may have impacted a completely unrelated report.  That is why we have a run set which allows for running a set of reports.
| Run Set | Description |
|---------|-------------|
| BASE_GEN_0000000_DOCGEN | Run a list of reports|

We can provide set of parameters and all reprots will be executed for that set.




