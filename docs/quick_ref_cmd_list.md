##Overview
This is a list of commands for quick reference.  These are the ones typically used by other tests.

##Code Translations
### BASE_GET_CODMST_DESC
This command can be used to get the translated text for an input code.  This is useful when developing UI tests where the screen needs input as description.  
For example, it can be used as follows to get the text of code trlr_typ.  The value passed in to trlr_typ is a code
````
 ##publish data where @* and colnam = 'trlr_typ' and codval = '@trlr_typ' |Script("BASE_GET_CODMST_DESC")##
````
