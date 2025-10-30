# Overview
This is a list of commands for quick reference.  These are the ones typically used by other tests.

## Code Translations
### BASE_GET_CODMST_DESC
This command can be used to get the translated text for an input code.  This is useful when developing UI tests where the screen needs input as description.  
For example, it can be used as follows to get the text of code trlr_typ.  The value passed in to trlr_typ is a code
````
 ##publish data where @* and colnam = 'trlr_typ' and codval = '@trlr_typ' |Script("BASE_GET_CODMST_DESC")##
````
* Input
    * colnam establishes the domain
    * codval is the value for which it finds the description
    * uc_return_colnam.  This is defaulted to lngdsc, but otherwise it can be passed in
* Output
Whatever is returned is the value to be typed in

#### Special Codes
Genrally it is going by the BY "codmst" but it has some special domains as well:
| Special colnam  | Special Input Parmeters     | Special Logic                   |
|-----------------|-----------------------------|---------------------------------|
| carcod          | uc_return_colnam = carnam   | Use "list carriers"             |
| ctncod          |                             | Use list carton codes where ctncod=@codval and wh_id=@wh_id |
| reacod          |                             | Use dscmst |
| cnttyp          |                             | Use list count type |

## General Purpose Values
### BASE_GET_GLOBAL_VALUE
This command can be used to properly get some global values formatted per our needs
* Input
    * uc_gui_filter_colexpr is special code for use with GUI.  we pass the input field along with value place-holder.  For value from context use &
* Outpit
    * Usable value

#### Examples
* when providing Web UI filters, we need to know the name of the field and the corresponding value from stack.  With those two use ````##publish data where @* and uc_gui_filter_colexpr = "'Transport Equipment='||&trlr_num"|Script("BASE_GET_GLOBAL_VALUE")##````
    * Here the name of the field is "Transport Equipment" we enclosed it in quotes
    * then we need to have an "="
    * "&trlr_num" implies that we read trlr_num from the context
 

### BASE_TRLR_FIND_EMPTY_DOCK_DOOR
This command can be used to find an empty door

* Input
    * The stack
* Output
    * stoloc
