# Task executor
#### Responsible for executing tasks.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/configuration.html#namespace-taskscheduler" target="_blank">Documentation</a>

(<b>Advanced</b>)

The executor created is a <i>ThreadPoolTaskExecutor</i>. Each submitted task is executed using one of possibly several <i>pooled threads</i>. The behaviour of the executor is specified by the <i>core</i> and  <i>max</i> size of the thread pool and the <i>queue size</i>.

When a task is submitted, the executor will first try to use a free thread if the number of active threads is currently less than the <i>core size</i>. If the core size has been reached, then the task will be added to the <i>queue</i> as long as its capacity has not yet been reached. Only then, if the queue's capacity has been reached, will the executor create a new thread beyond the core size. If the max size has also been reached, then the executor will reject the task.

Use the id <i>'taskScheduler'</i> to define the default task scheduler for this configuration. If this scheduler not is specified, a default scheduler will be created.

#### Queue capacity
Queue capacity for the executor. 

By default, the queue is unbounded, but this is rarely the desired configuration, because it can lead to <i>OutOfMemoryErrors</i> if enough tasks are added to that queue while all pool threads are busy. Furthermore, if the queue is unbounded, then the max size has no effect at all. Since the executor will always try the queue before creating a new thread beyond the core size, a queue must have a <i>finite capacity</i> for the thread pool to grow beyond the core size (this is why a fixed size pool is the only sensible case when using an unbounded queue).

Default when not specified: Integer.MAX_VALUE 
					

#### Keep alive
Keep-alive time in seconds. 

Inactive threads that have been created beyond the core size will timeout after the specified number of seconds elapse. If the executor has an <i>unbounded queue capacity</i> and a size range represented as 0-n, then the core threads will also be configured to timeout when inactive.
Otherwise, core threads will never timeout.
					

#### Rejection policy
Specifies the behaviour of the executor when a task is rejected.

The following pollicies are applied when a task is rejected: 
<b>1. Abort (Default)</b>
The executor will throw a <i>TaskRejectedException</i>.
<b>2. Caller runs </b>
The executor will force the thread that is calling the submit method to run the task itself.
<b>3. Discard </b>
Discard the rejected task silently.
<b>4. Discard the oldest.</b>
Discard the oldest unhandled task request.

<b>Usage</b>
 For applications where some tasks can be skipped under heavy load, either the <i>Discard Policy</i> or <i>Discard Oldest Policy</i> may be configured instead. Another option that works well for applications that need to throttle the submitted tasks under heavy load is the <i>Caller Runs Policy</i>. Instead of throwing an exception or discarding tasks, that policy will simply force the thread that is calling the submit method to run the task itself. The idea is that such a caller will be busy while running that task and not able to submit other tasks immediately. Therefore it provides a simple way to throttle the incoming load while maintaining the limits of the thread pool and queue. Typically this allows the executor to "catch up" on the tasks it is handling and thereby frees up some capacity on the queue, in the pool, or both. 


#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Pool size
Specifies the number of different tasks executed at the same time by this executor. 

Default when empty: '1-Integer.MAX_VALUE'

<b>(Advanced description)</b>
Specifies the core and the maximum thread pool size in order to
 limit the number of concurrent
 tasks.
 
If a single value is provided then the executor will have a fixed-size thread pool (the core and max sizes are the same). It also accepts a range in the form of "min-max". 

Eg.: 5-10



