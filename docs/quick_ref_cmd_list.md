# Overview
This is a list of commands and some tests for quick reference.  These are the ones typically used by other tests.

## Tests
### BASE_GEN_MANAGE_RUN_SET_CONTEXT
Since a run set has several steps - it is often a requirement to maintain some context between the steps.  We always have following arguments available for an execution:

| Argument               | Comments         |
|------------------------|------------------|
| call_typ_cd            | I is passed to initiatlize it. Else we clear the context.  When clearing we restore adjustment thresholds |
| uc_test_exec_seqnum    | Whenver a test or run set is executed, this gets a unique value.  It can be used to generate fresh data |
| wh_id                  | It can be passed explicitly.  If not then it is @@WH_ID |
| devcod                 | It can be passed explciitly.  If not then it is @@DEVCOD |
| usr_id                 | It can be passed explicitly.  If not then it is @@USR_ID |
| set_adj_thr_cst        | we can optionally pass in an adjustment threshold in terms of cost |
| set_adj_thr_unit       | we can optionally pass in an adjustment threshold in terms of units |
| stoloc                 | If passed in, we capture quantity |

We have following test cases
| Test Case        | Use             |
|------------------|-----------------|
| BASE_ALL_GEN     | Put as first step in a run set |
| BASE_GEN_CMPL    | Put as last step in a run set |


The conrext is maintained in the device_context table.  We get the next value for following sequences so that we can save
them here with the goal that at the end of the execution we can see what we did:

| Number Code (Sequence)  | What does it represent? |
|-------------------------|-------|
| exec_id                 | Deferred Execution Sequence |
| cnfrm_serv_id           | This represents execution of a workflow |
| dlytrn_id               | Daily Transaction Id |
| sl_evt_data_seq         | Event Data Sequence |


The device_context.devcod is set to

````
'UC_RUN_SET_CTXT_' || @uc_test_exec_seqnum
````

The table columns are set as follows

| dev_varnam             | Value          |
|------------------------|----------------|
| max_dlytrn_id          | Current value of sequence dlytrn_id |
| max_exec_id            | Current value of sequence exec_id |
| next_cnfrm_serv_id     | Current value of sequence cnfrm_serv_id |
| max_evt_data_seq       | Current value of sequence sl_evt_data_seq |
| adj_thr_cst            | for logged in user les_usr_ath.adj_thr_cst |
| adj_thr_unit           | for logged in user les_usr_ath.adj_thr_unit |
| uc_cur_untqty          | If stoloc was passed in, current unit quantity |

If set_adj_thr_cst or set_adj_thr_unit are passed, we set the data in les_usr_ath.  This approach comes in handy for
inventory counting and adjustment tests where we can force an approval flow.

### BASE_CLEAR_AUTEST_DEVICE_CONTEXT
device_context table is used by standard BY to maintain some key context values.  It is a good idea to always clear
this table for the device.  So we should call this test in the beginning of a run set.

| Argument               | Comments         |
|------------------------|------------------|
| wh_id                  | If not passed in default to @@WH_ID |
| devcod                 | If not passed in default to @@DEVCOD |

We have following test cases

| Test Case        | Use             |
|------------------|-----------------|
| BASE_ALL_GEN     | Put in the beginning of a run set |

This test will clear all rows in device_context table for the devcod

### BASE_GEN_POST_V001
This is a general purpose test which utilizes the device context table to publish data generated during a run set execution.
We place this toward the end of a run set.

| Argument                     | Comments         |
|------------------------------|------------------|
| wh_id                        | It can be passed explicitly.  If not then it is @@WH_ID |
| uc_test_exec_seqnum          | Whenver a test or run set is executed, this gets a unique value.  We use this to read device_context |
| uc_wait_for_deferred_exec    | If 1 then we wait for deferred execution to complete |
| uc_cnt_evt_val_expr          | We count events logged as variable uc_cnt_evt.  This is moca expression to use it |
| uc_cnt_evt_id_val_expr       | Distinct number of event ids is available as uc_cnt_evt_id.  THis can couunt those |
| uc_evt_id_val_expr           | A SQL expression (within case) to see if a specific event is logged.  Use evt_id |


We have following test cases

| Test Case        | Use             |
|------------------|-----------------|
| BASE_ALL_GEN     | Put in the beginning of a run set |

The test BASE_GEN_MANAGE_RUN_SET_CONTEXT saves some data in device_context.  This publishes
* If uc_wait_for_deferred_exec is 1, we wait for deferred executions to complete.  Then we publish the results
* Show events logged
* Show dlytrn data




## Commands
### BASE_GET_CODMST_DESC
This command can be used to get the translated text for an input code.  This is useful when developing UI tests where the screen needs input as description.  
For example, it can be used as follows to get the text of code trlr_typ.  The value passed in to trlr_typ is a code
````
 ##publish data where @* and colnam = 'trlr_typ' and codval = '@trlr_typ' |Script("BASE_GET_CODMST_DESC")##
````

#### Input

| Input Parmeter         | Description                 | Comments |
|------------------------|-----------------------------|----------|
| colnam                 | establishes the domain      | |
| codval                 | Value to look up            | |
| uc_return_colnam       | Name of column to publish   | |


#### Output
Whatever is returned is the value to be typed in

#### Special Codes
Genrally it is going by the BY "codmst" but it has some special domains as well:


| Special colnam  | Special Input Parmeters     | Special Logic                   |
|-----------------|-----------------------------|---------------------------------|
| carcod          | uc_return_colnam = carnam   | Use "list carriers"             |
| ctncod          |                             | Use list carton codes where ctncod=@codval and wh_id=@wh_id |
| reacod          |                             | Use dscmst |
| cnttyp          |                             | Use list count type |

### BASE_GET_STOLOC_FOR_FRONT_END
Locations have a concept of verrification code. This implies that we cannot type in location as our logic suggests instead we need
to first find its verification code and that is what we need to type in.  So when we have any field on Web UI or RF where we need 
to type in a location, we should always use this

#### Input

| Input Parmeter         | Description                 | Comments |
|------------------------|-----------------------------|----------|
| stoloc                 | Location we want to look up | Whatever location we want to type in |
| uc_return_colnam       | What should we publish      | Default is stoloc |

#### Output
We publish the location verification code if defined


## General Purpose Values
### BASE_GET_GLOBAL_VALUE
This command can be used to properly get some global values formatted per our needs

#### Input

| Input Parmeter         | Description                 | Comments |
|------------------------|-----------------------------|----------|
| uc_gui_filter_colexpr  | special code for use with GUI.  we pass the input field along with value place-holder.  For value from context use &      | |

#### Output
Usable value

#### Examples
* when providing Web UI filters, we need to know the name of the field and the corresponding value from stack.  With those two use

````
##publish data where @* and uc_gui_filter_colexpr = "'Transport Equipment='||&trlr_num"|Script("BASE_GET_GLOBAL_VALUE")##
````

    * Here the name of the field is "Transport Equipment" we enclosed it in quotes
    * then we need to have an "="
    * "&trlr_num" implies that we read trlr_num from the context
 

### BASE_TRLR_FIND_EMPTY_DOCK_DOOR
This command can be used to find an empty door

#### Input

| Input Parmeter         | Description                 | Comments |
|------------------------|-----------------------------|----------|
| @*                     | Stack is interpretted      | |

#### Output
* stoloc

