## Overview
Run Set Groups are used to define the basic unit for regression test.  A Run Set Group combines various Run Set Test Cases into a 
set and this set can then be executed from command line.

## Maintain Run Set Groups
* To view run set groups, see the "Run Set Group" tab in Smart MOCA Client AuTest

   <div style="text-align: center;">
  <img src="./Images/trainingtrack/P20.png"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
  </div>

* To add a run set test case to a group
    * Find the run set test case and press "Add To Run Set Group"
    
  <div style="text-align: center;">
  <img src="./Images/trainingtrack/p21.png"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
  </div>

    * Then add to an existing group or press "New Group" 
    
    <div style="text-align: center;">
    <img src="./Images/trainingtrack/p22.png"
        alt="undirectedmenu"
        style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
        onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
        ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
    </div>


    * Provide a name and description

    <div style="text-align: center;">
    <img src="Images/training_create_run_set_grp/training_run_set_grp_add_to_run_set_grp_button_new_dtl.jpg"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
    </div>
    
    * You can create a run set group with as many run set test cases as you want.  So lets also add BASE_NOOP to it
* Our sample run set group has two run set test cases 

<div style="text-align: center;">
    <img src="Images/training_create_run_set_grp/training_run_set_grp_sample_run_set_grp.jpg"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
    </div>

* If you press Execute it will execute all of the run set test cases

## Run as regression test
Typical reason for run set groups is to define regression test.  Once run set group is defined, it can be executed from comand line as follows:

* Find path to java on your machine.  You can open file %APPDATA%\SmartMOCAClient\config\smcagent\config.properties
    * For example ````C:\Program Files\Common Files\Oracle\Java\javapath\javaw.exe````
* You will need following parameters

| Command Line Argument   | Value                                          | Need to change? | Comments |
|-------------------------|------------------------------------------------|-----------------|----------|
| -cp                     | "mocadev.jar;lib\*;lib\selenium-java-4.33.0\*" | No              | |
|                         | com.oracular.mocadev.MOCADevLauncher           | No              | Always second parameter |
| security_key=           | Key that you provide in MOCA Client when you launch it | Yes     | This is the key you created.  It is required to be able to save passwords |
| moca_conn_id=           | Connection on the machine                      | Yes             | Connection created for the user running it |
| uc_run_set_grp_id_list= | List of run set groups                         | Yes             | What you want to run |

* For example, open a command promot and run

````
cd /d %APPDATA%\SmartMOCAClient\sw\smc
"C:\Program Files\Common Files\Oracle\Java\javapath\java.exe" -cp "mocadev.jar;lib\*;lib\selenium-java-4.33.0\*" com.oracular.mocadev.MOCADevLauncher "security_key=WHAT_YOU_CREATE_FOR_YOURSELF" moca_conn_id=WHAT_YOU_HAVE_IN_MOCA_CLIENT uc_run_set_grp_id_list=SIS_TMP1_SAMPLE
````

* You can create a new key if you want for running as regression test
* Put parameters in quotes as indicated

---
<br>