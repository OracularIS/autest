## Overview

Smart AuTest is a comprehensive automated testing suite that requires no installation footprint. The metadata and results are stored in the cloud, where the security mechanism is tenant-based.

The test metadata primarily follows a low-code solution where tests are executed by abstractly representing the scenarios using data.

## About Test Data

Understanding how we should manage the test data is central to the whole project. Our vision is that customers can start using the solution immediately and require little day-to-day maintenance. We suggest the following paradigm to support this vision:

- Whenever a test is run, the framework always pushes a globally unique, base-36 string to the stack. This allows us to generate new data that is guaranteed to be unique. The name of this parameter is `uc_test_exec_seqnum`.
- The test run sets utilize this concept to simplify the process of reusing the various components.
- This strategy also simplifies managing the test data.  We often have the test cases defined in spreadsheets - the Smart IS strategy suggests that we represent the same test cases as actual objects in the WMS instance.

### Type of Data
Following section provides details about the various types of data and how the template data should be managed for each:
#### Inbound
##### ASN (receipts with or without inventory data)
This is the most common receiving scenario where we have RCVTRK, RCVINV, RCVLIN, INVDTL, INVSUB, and INVLOD data.  In business terms this represents the scenario where the shipping or manufcaturing side sent the detailed data to the WMS.  Smart IS test data methodology suggests that:
- Identify some real master receipts (RCVTRK.TRKNUM) that represent the business use cases.
- Then copy that to serve as a template.  Unfortunately there is no standard screen available for this.
    - You can use the following snippet to copy an existing master receipt
      ```sql
         publish data
         where uc_src_trknum = '<provide the soruce rcvtrk.trknum>'
         and new_trknum = '<provide the new truck we want to create - to serve as a sample>'
         and uc_copy_rcvtrk_inv_flg = '1' /* 1 means that we copy inventory for the source truck as well.  This helps in properly representing an ASN */
         and uc_generate_new_invtid = '1' /* 1 means that when copying inventory, it will create new identifiers from sysctl */
         and uc_set_asnflg_on_invdtl = '1' /* 1 means that invdtl will be marked as ASN */
         and uc_new_ser_num_expr = "@ser_num||'-'||@dtlnum" /* if we had serials, the new serials will be created using this expression */
         |
         {
             /*
              * uc_new_trknum_expr defines how the record is created.  So it will use what was provided above
              * uc_new_invnum_expr defines how he new RCVINV is creted.  Per this, the invnum of the source will be used in the new record
              * uc_new_ponum_expr defines the ponum field value.  Per above it will be kept the same as source
              */
             publish data
             where uc_new_trknum_expr = "'" || @new_trknum || "'"
             and uc_new_invnum_expr = "@invnum"
             and uc_new_ponum_expr = "decode (@po_num,null,null,@po_num)"
             |
             {
                 Script("BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001_EXEC")
             }
         }
      
- The copied master receipt, that will serve as a template, should follow following naming convention:
  | Concept          | Rules |
  |------------------|-------|
  | Master Receipt (trknum) Prefix | `RCVSMP` |
  | Do not receive it | The RCVLIN data should be as if it is not yet received.  So rcvqty should be 0 |
  | Example          | `RCVSMP001`, `RCVSMP002`.  You may also append after the prefix something meaningful to represent the scenario |
When the Smart auTest suite processes such tests, following concepts come into play:
- The tests start by providing the template master receipt number (RCVTRK.TRKNUM).  The user should provide an exact value.
- This data is copied to a new data structure that follows following conventions:
  |  Data Element    |  Rules    |
  |------------------|-----------|
  | Master Receipt (trknum) Prefix | `ARTRK-` prefix.  The suffix is `-` follwed by the generated test execution number  |
  | Invoice Number (invnum) | The rcvinv.invnum of the template master receipt will become a prefix followed by a `-` and then the test execution number |
  | PO Number   |If the source master receipt had a po number, then the copied data will have a new po number with source po number as prefix followed a `-` and then the test execution number |
- If this ASN has inventory data as well:
  |  Data Element    |  Rules    |
  |------------------|-----------|
  | Load Number | Load number of the source master receipt followed by `-` and then the test execution number  |
  | Sub Number | Sub number of the source master receipt followed by `-` and then the test execution number  |
  | Detail Number | Detail number of the source master receipt followed by `-` and then the test execution number  |
  | Serial Number | Serial number of the source master receipt followed by `-` and then the test execution number  |
- If the source ASN inventory detail had a hold, then the new copied inventory detail will have the same hold - but with a new generated hold number.

These protcols allow the tests to run in a smooth way.  We always start from a known test case (template) and can run through all the steps in a predictable fashion.

##### Receive Invoice Master (RIM)
This represents the use case where we have receive invoice master data that is stored in RIMHDR and RIMLIN tables.
- Identify some real business data (RIMHDR.INVNUMM) that represent the business use cases.
- Then copy that to serve as a template.  Unfortunately there is no standard screen available for this.
    - You can use the following snippet to copy an existing master receipt
      ```sql
      publish data
      where uc_src_invnum = '<provide the soruce rcvtrk.trknum>'
      and new_invnum = '<provide the new truck we want to create - to serve as a sample>'
      and uc_create_rcv = '0'
      |
      {
          publish data
          where uc_new_invnum_expr = "@invnum"
          |
          {
              Script("BASE_INB_0001050_COPY_TEMPLATE_RIM_MOCA_V001_EXEC")
          }
      }
- The copied receive invouce master, that will serve as a template, should follow following naming convention:
  | Concept          | Rules |
  |------------------|-------|
  | RIMHDR.INVNUM | `RIMSMP` |
  | Do not receive it | Do not create RCV structure for it |
  | Example          | `RIMSMP001`, `RIMSMP002`.  You may also append after the prefix something meaningful to represent the scenario |
When the Smart auTest suite processes such tests, following concepts come into play:
- The tests start by providing the template receive invoice master  (RIMHDR.INVNUM).  The user should provide an exact value.
- This data is copied to a new data structure that follows following conventions:
  |  Data Element    |  Rules    |
  |------------------|-----------|
  | Receive Invoice Master Prefix | `ARINV-` prefix.  The suffix is `-` follwed by the generated test execution number  |
- The test will also create a RCV structure for it:
  |  Data Element    |  Rules    |
  |------------------|-----------|
  | rcvtrk.trknum | `ARTRK-` prefix.  The suffix is `-` follwed by the generated test execution number   |
These protcols allow the tests to run in a smooth way.  We always start from a known test case (template) and can run through all the steps in a predictable fashion.

#### Outbound

##### Orders
This covers the common scenario where the outbound flow in the WMS starts with an order.  The orders are typically downlaoded into the WMS.  Smart IS test data methodology suggests that:
- Identify some real orders that represent the business use cases.
- Simplify the orders if possible.  For example the real order may have a large number of lines - we should simplify it if possible.
- Then copy that real order as a template order:
   - You can use the UI to copy the order.  You may also use the "copy order" MOCA Comamnd.
   - Then copied order, that would serve as a template, should follow the following naming convention
     | Concept          | Rules |
     |------------------|-------|
     | Order Prefix     | `ATST-TMPL-`  **We stronlgly recommend that this exact prefix is used which has length of 10.  This makes the copy order process yield meaningful test order numbers.** |
     | Other attributes | We suggest that `ord.template_flg` is 1 so that these are easy to identify |
     | Example          | `ATST-TMPL-TEST001`, `ATST-TMPL-TEST002`.  You may also append after the prefix something meaningful to represent the scenario |
When the Smart auTest suite processes such tests, following concpts come into play:
- The user provides the template order number.
    - Note that user can alsp provide wild card expression.  When that happens then we copy all orders that match the wild card to new order numbers
    - **And then the copied orders are put into the same wave**
- The copied order number follows the following conventions:
  |  Data Element    |  Rules    |
  |------------------|-----------|
  | Order Number     | `ADATA-` prefix.  The suffix is `-` follwed by the generated test execution number.  The part of the template order number starting at position 11 is also part of this order number  |
  | Wave Set         | `ord.wave_set` is set to the same value for all orders that are processed together.  The wave set is set to `AW-` followed by the test execution number for this run |
  | Wave             | `schbat` is set to `ADATAW-` followed by the test execution number |
- **We can provide an explicit order number when running the test as well**
    - There are scenarios where we want to process an exact order.  For example, host may send a specific order that we need to complete.  For those scenarios, we can simply provide the order number as "New Order Number"
    - The concepts described above regarding setting ord.wave_set and wave name still apply

These protcols allow the tests to run in a smooth way.  We always start from a known test case (template) and can run through all the steps in a predictable fashion.


##### Traffic Plans (Carrier Moves)
This covers the common scenario where the outbound flow in the WMS starts with a complete traffic plan.  This means that we have car_move, stop, shipment, shipment_line, ord, ord_line data already. Smart IS test data methodology suggests that:
- Identify some real traffic plans that represent the business use cases
- Simplify the orders if possible.  For example the real order may have a large number of lines - we should simplify it if possible.
- Then copy that traffic plan as a template:
    - Note that we do not have to copy it.  See the section below - all we need to do is set the car_move.host_ext_id
    - The copied data should follow following conventions:
      | Concept          | Rules |
      |------------------|-------|
      | Carrier Move Host External Id  | The car_move.car_move_id does not matter.  The car_move.host_ext_id will identify it as a sample.  Name it with a prefox `CMSAMPLE` and put a reasonable suffix |
      | Other | Leave this carrier move in an unprocessed state |
      | Example          | `CMSAMPLE001`.  You may also append after the prefix something meaningful to represent the scenario |
When the Smart auTest suite processes such tests, following concpts come into play:
- The user provides the template load number (car_move.host_ext_id)
- The copied data follows the following conventions:
  |  Data Element    |  Rules    |
  |------------------|-----------|
  | Carrier Move Id  | This is generated based on sequence car_move_id |
  | car_move.host_ext_id | `ADATA-` followed by the host_ext_id of the template.  Then `-` and then the test execution number for this run |
  | stop Id | This is generated based on sequence stop_id |
  | Shipment Id | This is generated based on sequence ship_id |
  | Order Number     | `ADATA-` prefix.  Then the source order number.  Then `-` and  then the test execution number for this run  |
  | Wave Set         | `ord.wave_set` and `shipment.wave_set` is set to the same value which is `AW-` followed by the test execution number for this run |
  | Wave             | `schbat` is set to `ADATAW-` followed by the test execution number |
These protcols allow the tests to run in a smooth way.  We always start from a known test case (template) and can run through all the steps in a predictable fashion.


#### Inventory Operations
We may want to perform some inventory operations to validate that the various operations are working correctly.  The strategy mentioned above is not suitable for such scenarios.  Smart IS test data methodology suggests that:
- We **create** some template test locations in the environment to test certain special scenarios.
    - For example, we can create some special locations in a typical area/zone in the test environment for special tests.
    - Ideally we should create a new area/zone so that we can seggregate it easily
 - We have a standard run set called `BASE_INV_A00000_INV_OPS` which would then peform several inventory operations
    - We can pass it a "Soruce Location" and "Destination Location".  The script would move inventory back and forth.
    - It allows us to a coma-separted list of statuses.  It will move inventory through all statuses provided.
    - It will also do partial inventory moves

#### Count Operations
We may want to perform counts to validate that the use cases are working correctly.  Smart IS test data methodology suggests that:
- While the standard product creates counts using its own naming convention, **we rename the cntwav and cntbat to include test execution number**
  |  Data Element    |  Rules    |
  |------------------|-----------|
  | Count Wave (cnthdr.cntwav)  | We update it to `ACNTWAV-` follwed by the test execution sequence number formatted as a 6 digit base-36 value with leading 0s.  |
  | Count Batch (cntbat)  | We update it after it is generated but keep the generated value in the name as well.  We **prefx** the cntwav value.   |
  | Example Count Wave | Count Wave `ACNTWAV-0000YH` |
  | Example Count Batch | Say the system generated a count batch of CID00007MQ and we have detremined count wave of `ACNTWAV-0000YH`.  We will update the cntbat to `ACNTWAV-0000YH--CID00007MQ` |

These protcols allow the tests to run in a smooth way.  The count batch becomes a predictable value which allows us to control the execution.

## Global Metadata

As part of the auTest subscription, you have access to a rich set of commands, tests, test cases, and run sets. They will show up in the suite as `world` tenant and are named with the `BASE_` prefix.

![](Images/image2.png)


We are always working on enriching this set, and you will always have access to the latest set as part of the subscription.

While customers can create their own metadata, at Smart IS, we strive to make this set as comprehensive as possible so that customers can simply use these on day one.

You can see the available tests here: [Packaged_Tests](./packaged_tests.md)

## Commands

We need to provide specific instructions at various points to influence the execution. These are referred to as “Commands”. We have the following categories of commands:

- The core logic of MOCA-based tests is represented in MOCA snippets.
- The validation commands are MOCA snippets as well.
- We can use the snippets to set the values of the arguments.

To improve reuse, the commands can call other commands as well by using the `Script` keyword. For example, in the snippet below, the command is calling another command: 
  - `
  { publish data where dstloc = @nxtloc 
    |
    Script("base_inv_load_deposit_v001") } `
    
When using the commands in various contexts, we can either mention them by name or by using special syntax, for example: 

publish data where uc_src_trknum = `'RCVSMP001'` and uc_return_colnam='prtnum' | Script(`base_get_ossibot_rcv_id_detail`) 

## Providing Values for Arguments

When providing values for the arguments in various contexts, we have the following capabilities:

- We can provide a literal value
- We can call a `command` by using ## syntax mentioned above
  - Within this context, we can use `Script` capability to call any command.
- We can use `[<function key>]` to press any function key
- We can use `[Enter]`
- We can scrape anything from an RF form using `<<>>` syntax. Within this, we put the name of the field or form.field.

## Application Flow Step (Non MOCA Tests)

As our vision is a `low-code` solution, we have introduced a concept of `Application Flow Step` which represents the front-end use cases in the form of data.

| Application Flow Step Id | Type          | Description                       |
|--------------------------|---------------|-----------------------------------|
| IDENTIFY_LOAD            | RF Form       | This represents an RF form        |
| ENTER_TEXT               | RF Form Action| This will allow us to enter text  |
| wm.outboundplanner/wm.wavesandpicks | WEB Form      | This is how we call a web form    |
| ACTION                   | WEB Action    | This performs an action on the web UI |
| FILTER                   | WEB Action    | This uses the filter on the web   |
| SAVE                     | WEB Action    | Indicates that we press save      |
| CLOSE                    | WEB Action    | Indicates that we closed a form   |
| CLICK                    | WEB Action    | Indicates click action            |
| CLICK_LINKS              | WEB Action    | Indicates clicking a link         |
| CLICK_TABLE_CELLS        | WEB Action    | Indicates clicking a table cell   |
| BUTTON                   | WEB Action    | Indicates pressing a button on the web |

This data is pre-populated for the `world` tenant. Furthermore, we know which versions a specific form exists in. Smart IS maintains this metadata.

We also know what arguments are available for each step, i.e.

- For any web or RF form, we know the fields available on the form.
- It is possible to provide default values here.

Note that custom forms can be loaded into this as well. The auTest suite allows for uploading custom form data. Such data is then loaded into a tenant-specific area.

## Application Flow (Non MOCA Tests)

This list will include a row for every web-based or RF-based flow at the lowest level. For example, we represent one form-interaction. These are then brought together in a test to represent a use case. Each RF form or web form makes up a row here, for example:

| Application Flow Id | Type | Description             |
|---------------------|------|-------------------------|
| AF_IDENTIFY_LOAD    | RF   | To identify a single load |
| WEB_PLAN_WAVE       | WEB  | To Plan a wave          |

Each application flow can describe the arguments for it.

## Application Flows have Steps (Non MOCA Tests)

As mentioned above, we have the steps already. When we define an application flow, then we add multiple steps to the flow. When adding this – we can add steps or another application flow as well.

For example, we have an application flow called AF_LOAD_ID_V002 which can be used to identify a load. It is defined as follows:

- `IDENTIFY_LOAD` - implying we call this RF Form
- `IDENTIFY_LOAD_PART` - implying that this RF form can become the next form
   - Since it shows up conditionally, we have a `pre-condition` for this defined as `<<FORM_NAME>> = IDENTIFY_LOAD_PART`
- `UDIA_CAPTURE` - implying that this form can also come next
    - Since this is also conditional, we have a pre-condition of `<<FORM_NAME>> = UDIA_CAPTURE`

Above flow describes the main identify flow. Then we have another flow that calls it. This flow is called AF_LOAD_ID_MAIN_V002 and it has the following:

- `UNDIR_IDENTIFY.LOAD_IDENTIFY`. This is how it knows that the framework needs to look up the menu structure and find a path to this form
- And then it calls `AF_LOAD_ID_V002` - implying it calls the identify flow we created above.

Web UI application flows follow the same concepts. For example, we have an application flow called BASE_WEB_PLAN_WAVE_V002 to plan a wave. It has the following:

- Call step `wm.outboundplanner/wm.wavesandpicks` - this is enough to tell the framework to launch the form.
- `CLICK_LINKS` - indicates we have to click a link after that.
  - For its data, we tell it “Actions, Plan Wave” - which drives what is clicked
- We have `ENTER_TEXT`
  - We say that `VARNAM` is `ruleName`
  - And we use `@uc_wave_rule_nam` indicating the value of the rule name
- We have another `ENTER_TEXT` step
  - We say that `VARNAM` is `wave_set`
  - And for its value, we have an expression that calls a script. This script will return the wave name to use per our conventions:
    - `
      ##publish data where @* and uc_return_colnam='schbat'|Script("base_get_ossibot_hdr_key_data")##
      `
- Then we have “BUTTON”
  - We find the button by saying “TEXT” is “Search”
- Then we have another “BUTTON” step
  - We say that the “TEXT” this time is “Plan Wave”
- Then we have another text box
  - The name of the text field is “waveNumber” and for its value we use a command:
    - `
      ##publish data where @* and uc_return_colnam='schbat'|Script("base_get_ossibot_hdr_key_data")##
      `
- Then we press another button
  - The button text is `OK`

The above illustrates how we can author tests in a `low code` regime.

## Test (All categories – MOCA, RF, Web UI)

At the lowest level, we define tests. Tests are defined by:

- A name
- Type of tests: MOCA, WEB, RF
- We provide the following commands
  - For MOCA based tests, the main command is provided that does the work
  - A command that is run before the test is launched
  - A command that is executed after the test has run
  - A command to validate the results.
- Expected time of the execution of this test
- If it is an RF or Web UI test, then the test has `test steps`. The steps point to application flows we have created earlier.

So the test becomes a central concept which represents MOCA, RF, and Web UI based tests.

## Test Case

Whereas a test provides the logic and possible input – a test case provides specific input for the various arguments.

## Run Sets

Run Sets combine various test cases so that they can be executed in a sequence to represent a complete use case. The run set can combine tests of various technologies.

