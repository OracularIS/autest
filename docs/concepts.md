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

| Data Type                  | Rules                                                                                  |
|----------------------------|----------------------------------------------------------------------------------------------|
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

