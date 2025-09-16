# Maintenance Layer 

The Maintenance Layer serves as the foundation of Autest, where all test artifacts are created, updated, managed, and stored. 

This is facilitated through **SmartApps**, a centralized, cloud-based web application designed for the unified management of Blue Yonder product configurations and test metadata.

SmartApps is responsible for several key functions, including:

#### 1. **Centralized Metadata Management**
SmartApps acts as the central repository for all testing components. These include:
- **Test Cases**: Define the individual testing logic for a specific scenario or function. Each test case can include multiple steps and validations.

  <div style="text-align: left;">
       <img src="./Images/testcase.png"
              alt="undirectedmenu"
              style="height: 200px; margin: auto; display: block; cursor: zoom-in;
                     border: 2px solid #000000; border-radius: 4px;"
              onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
              ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
       </div>

- **Tests**: The most granular unit in Autest. A test is an individual script or action that performs a specific check or task.

  <div style="text-align: left;">
       <img src="./Images/test.png"
              alt="undirectedmenu"
              style="height: 200px; margin: auto; display: block; cursor: zoom-in;
                     border: 2px solid #000000; border-radius: 4px;"
              onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
              ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
       </div>

- **Commands**: Scripts or reusable blocks of logic that define test flows, actions, or operations to be performed during testing.

  <div style="text-align: left;">
       <img src="./Images/command.png"
              alt="undirectedmenu"
              style="height: 200px; margin: auto; display: block; cursor: zoom-in;
                     border: 2px solid #000000; border-radius: 4px;"
              onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
              ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
       </div>
 
- **Runsets**: Groups of test cases bundled for sequential or parallel execution. Runsets are useful for managing larger test cycles or regression test suites.

  <div style="text-align: left;">
       <img src="./Images/runset.png"
              alt="undirectedmenu"
              style="height: 200px; margin: auto; display: block; cursor: zoom-in;
                     border: 2px solid #000000; border-radius: 4px;"
              onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
              ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
       </div>
 
#### 2. **Full Lifecycle Control**
Users can:
- **Create**: Define new test cases, commands, and runsets from scratch, with support for step-by-step building and metadata tagging.
- **Update**: Modify existing test cases or commands to reflect changes in business processes or application logic.
- **Remove**: Retire outdated or redundant test definitions, keeping the environment clean and up-to-date.
- **Reuse**: Leverage the Copy feature to duplicate and adapt existing test cases or commands, promoting modular design and faster test creation.

#### 3. **Packaged and Custom Tests**
- Autest provides a library of **packaged test cases** aligned with standard BY processes.
- Users can also build **customized tests** tailored to their organization's specific workflows, using a no-code/low-code interface within SmartApps.

#### 4. **Result Visualization**
SmartApps provides a dedicated **Autest Dashboard** that offers clear and comprehensive visibility into execution results. Users can easily:

- View the number of passed and failed tests
- Filter results based on where the test was performed, MOCA or RF 
- Monitor execution time and trends
- Compare results across different runs or timeframes

<div style="text-align: left;">
  <img src="./Images/maintenance1.png"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
   </div>
 

This visual representation makes it simple for users to track test performance, identify issues quickly, and measure the impact of changes over time, all without needing to dive into raw logs or reports.

### Benefits of the Maintenance Layer:
- **Cloud-Based Accessibility**: SmartApps is accessible from any location with an internet connection, supporting distributed QA teams.
-  **High Reusability**: Once created, test components such as commands, test cases, and runsets can be reused across multiple scenarios. This reduces duplication, saves time, and ensures consistency throughout the testing process.

- **User-Friendly Interface**: Designed for functional testers and QA analysts, reducing dependency on developers.
- **Test Versioning & Governance**: SmartApps supports metadata versioning and audit history, ensuring traceability and control.
- **Efficiency through Reusability**: Encourages reuse of scripts and logic across multiple test scenarios.

---

<br><br>