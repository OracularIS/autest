## Creating MOCA Based Tests

This section describes the steps involved in MOCA based tests:

### Get Traces

When developing MOCA based tests, we want to execute the MOCA commands that are as close to the ones executed by the front-end as possible. This is to make sure that our test coverage is as close to the real world as possible.

If the use case involves RF, then getting an MTF trace is a good first step as that shows the MOCA commands easily. Refer to the concepts section above to see how you can use traces to find appropriate commands.

### Decide Which Commands to Use

It may not be important to run every command that the client issued. Generally, we are interested in only those commands that changed the state of the underlying data.

There are exceptions to this rule though. For example, in some cases, it is possible that a “read” command has an error which fails the front-end. But generally, we want to take the middle path and as a first pass only focus on the commands that changed the state. If then we find that we missed something, we can add those “read” commands in the test as well.

### Decide on What Test You Will Create – One Use Case May Create More Than One Test

When we execute tests, we typically run them as part of a run set. A run set has details where each row represents a test case (a test case is a test with some pre-defined data).

It helps if we create smaller tests so that they are easily manageable and then string them together in a run-set. For example, the following run set shows how we receive a truck:

![Receive a Truck](#)

And the following shows how we process an outbound order:

![Process an Outbound Order](#)

You can see that we have created tests at a manageable level and then we string them together for the final run set.

### Decide on the Arguments That You Need for the Test

We need to then decide on the arguments for the test. There are certain arguments that are always there (see concepts above). In addition to that, we will have certain arguments that are based on the specific test or based on the type of run set that it will be called from. Please note:

To simplify development and testing of the testing script, you can create optional arguments that you default intelligently.

Understand the concept of `uc_test_exec_seqnum`. This is central to how we write tests. We always go by the idea that we have some template data and when running the test we copy from that template to the new data and then use it. That is why we typically have a “copy” test case as the first one in our run sets. But at the same time, we want to also support the idea of passing in explicit values as well to cover any specific scenarios.

Decide input as expressions where appropriate – but at the same time, allow for exact input as well.

### Decide on What Data Will This Test Run On

In some cases, we will process one row – but for MOCA based tests, we will often create them to process a set of data. For example, we may process all inventory in a truck and deposit to a destination.

If we decide to work on more than one row, then it is a good practice to allow for optional input variables to limit how much data is processed. For example here I am defining that I want to process a single row.

```moca
publish data
    where uc_autest_comflg = 1
    and uc_max_rows = 1
```
Then later on I can use `uc_max_rows` to limit the results of a query or use other techniques like “session variables” to limit the processing to a single row.

## Decide if Our Test Needs to Support Stress Testing

Every test is not automatically a candidate for being run as a stress test. To be run as a stress test, we need to make sure that the code has appropriate logic to “lock” and with “nowait” (see concepts above). The test should then also respect `uc_stress_test_mode` to make determination and then should process one row of data.

## Decide if Our Test Will Do a Commit or Rollback

As a general rule, we do not want to do commit or rollback inside a test script. If in a certain case we want to do this as part of a test, then we should make it controllable via input arguments.

The reason for doing commit or rollback will be to support stress testing and free locks such that it represents reality. For example, if we are going to pick up loads and deposit them as part of a script, it is a good idea to commit after pick and then after deposit as that is how the transaction works in reality. If we did not do that, then we would create artificial contention.

## Decide if Your Script Needs to Include a Random “Sleep”

It may be important in some cases to include a sleep inside the script. Typically that will be needed to support stress testing. If needed use `Thread.sleep` or the “go to sleep” MOCA command. But it is a good idea to define an optional input variable that must be set to do this.

## Decide on the Output of the Test Script

When our scripts run, their output is captured and recorded as part of the run. So the output becomes extremely valuable when we want to refer to the execution later.

With that understanding, we should not be stingy in terms of the output we create for the scripts.

Enclose each logical “step” of your test in a pair of braces. And then at the end of your logic, publish data that reflects the work done. Also refer to the concept above about capturing the timing. For example:

```moca
 - 
start_ms = System.currentTimeMillis() catch(@?)

{
  <your logic>;
  end_ms = System.currentTimeMillis() catch(@?)
  |
  publish data
  where step = 'my step name'
  and <data that describes what the step did>
  and elapsed = @end_ms - @start_ms
}
```
 - Use `“&”` for each logical “step” inside your test script, for example: 
```moca{ 

<step 1> 

} 

& 

{ 

<step 2> 

} ```
