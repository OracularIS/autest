# Execution Analytics

The **Execution Dashboard** in AuTest offers a rich, visual representation of test performance metrics over time.

It enables QA teams to monitor progress, identify bottlenecks, and make data-driven decisions to improve testing quality and coverage.

To access the dashboard, navigate to:  
**`Autest → Executions → Dashboard`**

<div style="text-align: left;">
  <img src="./Images/dashboard1.png"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
   </div>

## Key Insights Available on the Dashboard

Below are the main insights you can explore on the dashboard, offering a comprehensive overview of Autest execution dashboard.


### Execution Summary

- **Total Executions**: Displays the complete number of executed tests during the selected date range.
- **Success Rate**: Shows the percentage of passed tests visually, including exact counts.
- **Passed vs Failed**: A clear breakdown of successful and failed test cases.

<div style="text-align: left;">
  <img src="./Images/dashboard2.png"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
   </div>

### Test Types Breakdown

A **pie chart** view showing test executions by category:
- ADHOC
- REGRESSION
- STRESS

<div style="text-align: left;">
  <img src="./Images/dashboard3.png"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
   </div>

This helps identify the types of testing that are most frequently performed.

### Tests Run by Type

A **bar graph** comparing execution results by platform:
- MOCA
- RF
- WEB

<div style="text-align: left;">
  <img src="./Images/dashboard4.png"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
   </div>

Each platform shows **Passed** (green) vs **Failed** (red) tests to give a quick status of test reliability.

###  Execution Trends Over Time

This **line graph** tracks the total execution time (in milliseconds) month by month.

<div style="text-align: left;">
  <img src="./Images/dashboard5.png"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
   </div>

It helps:
- Identify high-load months
- Spot unusual trends or spikes
- Optimize execution planning

###  Success/Failure by Date

A **stacked bar chart** showing the number of passed and failed test executions per month.

<div style="text-align: left;">
  <img src="./Images/dashboard6.png"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
   </div>

Great for:
- Tracking improvements in test success rates
- Spotting problematic periods
- Visualizing stability over time

### Module-Wise Test Execution

This section shows which WMS modules are being tested the most, and how each performs.

Examples include:
- **INBOUND**
- **INVENTORY**
- **OUTBOUND**
- **ORDER**

<div style="text-align: left;">
  <img src="./Images/dashboard7.png"
       alt="undirectedmenu"
       style="height: 200px; margin: auto; display: block; cursor: zoom-in;
              border: 2px solid #000000; border-radius: 4px;"
       onclick="this.style.height='400px'; this.style.cursor='zoom-out';"
       ondblclick="this.style.height='200px'; this.style.cursor='zoom-in';">
   </div>

You’ll see a **line chart** that compares **Passed vs Failed** test cases per module.

## Key Benefits of the Dashboard

- **Real-Time Visibility** into testing progress and issues
- **Platform-Based Comparison** for identifying where failures occur
- **Clear Trends** across execution time and module-wise testing
- **Exportable Data** for reports and analysis
- **User-Friendly Filters** for customizing views by date range


> Need help exporting results or analyzing failures? Head over to the [Results Page](./results.md) for detailed instructions.

---
<br>
