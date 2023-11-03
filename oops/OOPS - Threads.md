## Life Cycle
- New
- Active - start()
	- runnable
	- running
- wait - `wait()`, `join()`
- timed wait - avoids startvation - `wait(<ms>)`, `join(<ms>)`, `sleep(<ms>)`
- blocked
- Terminated
	- End of `run()`
	- Interrupt

#### Creating a thread:
```java
Thread <thread_name> = new Thread();
```

> Call stack is allocated for every function that is being executed in the stack segment of run.

