##Overview

##Example
We will work through following example
* Open "Transport Equipment Screen" ![Transport Equipment](Images/create_web_ui_test/transport_eqipment_main.jpg)
* Capture the code we need to call it independently.  This is in the URL after the `#`.  For example
````
http://BLAHBLAH/portal?siteId=ABC&subsite=ABC#wm.shipping/wm.transportequipment////
````
The name needed to launch this is "**wm.shipping/wm.transportequipment**"
* See if the form has multiple buttons or tabs which may require us to select one all the time.  For example this form has "Transport Equipment" and "Tractors" button.  But we can ignore this as the one that is selected is what we want
* We want to create a new trailer first.  So we need to press Actions and then selct "Add Transport Equipment" ![Transport Equipment Actions Add](Images/create_web_ui_test/transport_equipment_actions_add.jpg)
Note down the exact text, i.e. "Add Transport Equipment"
* A new form now shows up [Transport Equipment Add Dialog](Images/create_web_ui_test/transport_equipment_dialog_add.jpg)
* During add we need to set several fields here.  We will need to record the _names_ of those controls.  In Chrome, you can right click on a control and then choose "Inspect".  For example navigate to "Equipment Number", right click and choose Inspect ![Right Click Inspect](Images/create_web_ui_test/transport_equipment_dialog_add_right_click_inspect.jpg).
  * Then see the name of the field.  For example, in this case the name is "trailerNumber"
    ![Inspect See Trailer](Images/create_web_ui_test/transport_equipment_dialog_add_field_trlr_num.jpg).  Using this technique find the names of all the fields that you want to control.  In this case we have
      * trailerNumber (Equipment Number)
      * carrier (Carrier)
      * trailerCode (Use)
* For each field that you want to enter the value for, see if the value is supposed to be a "code" or can it be passed in as text.   For example you will notice that for carrier you need to provide the carrier by name  but most likely the input for the test is supposed to be carrier code.   Same for trailer code and railer type.  
