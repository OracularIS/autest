## Overview
This training is to get familiar with viewing execution results.  We can view results from MOCA Client AuTest or from the web

## View From Smart MOCA Client AuTest
* Highlight the run set and press Results 

  <div style="text-align: center;">
  <img src="./Images/trainingtrack/p14.png"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
  </div>


* Validate the filter fields

  <div style="text-align: center;">
  <img src="Images/training_view_results/training_view_results_moca_client_press_filter_fields.jpg"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
  </div>



| Filter Field    | Description                     | Comments |
|-----------------|---------------------------------|----------|
| Tenant          | Tenant that we want to look up  | Available if you have access to multiplle tenants |
| Run Id          | The run set id                  | If we had one selected, it is defaulted |
| Test            | Filter for a specific test      | Applies if test is run stand-alone |
| Test Case       | Filter for a specific test case | Applies if test is run stand-alone |
| Remote Server   | The name of the connection      | Defaulted to one we logged in with |
| Run#            | Every execution is assigned a sequence | |
| Status          | Filter for a specifc error      | 0 implies success |
| Error           | Dropdown                        | Allows for easily filtering for failed runs |
| Start Date      | Filter date                     | Runs since this date are displayed |

* Pressing Find displays the results 

  <div style="text-align: center;">
  <img src="Images/training_view_results/training_view_results_moca_client_result_grid.jpg"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
  </div>

* Select a row
    * Below we will see the arguments the run set was executed with 

  <div style="text-align: center;">
  <img src="Images/training_view_results/training_view_results_moca_client_result_args.jpg"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
  </div>

    * To see more data, double click on the selecte row
    * It will display the same results as were displayed when test was executed.  Refer to Run Set execution training 
   

      <div style="text-align: center;">
      <img src="Images/training_view_results/training_view_results_moca_client_result_dtl.jpg"
          alt="undirectedmenu"
         style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
       </div>

  ## View From Web
  * Login to the Smart Apps
  * Select Results tab 
     <div style="text-align: center;">
      <img src="./Images/trainingtrack/p18.png"
          alt="undirectedmenu"
         style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
       </div>

  * Use filter row.  It will show results
  * Select a row and press "Export" to see a PDF of the execution 
  
     <div style="text-align: center;">
      <img src="./Images/trainingtrack/p19.png"
          alt="undirectedmenu"
         style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
       </div>

  * This will export a PDF for the whole execution. 
  
   
