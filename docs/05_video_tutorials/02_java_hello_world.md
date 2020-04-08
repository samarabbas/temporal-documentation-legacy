# Java Hello World Workflow Implementation

Source code:

```java
public interface HelloWorkflow {
    @WorkflowMethod(executionStartToCloseTimeoutSeconds = 300)
    String getGreeting(String name);
}
```
```java
package com.tutorial;

import io.temporal.workflow.Workflow;

import java.time.Duration;

public class HelloWorkflowImpl implements HelloWorkflow {
    @Override
    public String getGreeting(String name) {
        Workflow.sleep(Duration.ofMinutes(1));
        return "Hello " + name + "!";
    }
}
```
```java
package com.tutorial;

import io.temporal.worker.Worker;

public class Main {

    public static void main(String[] args) {
        Worker.Factory f = new Worker.Factory("samples-namespace");
        Worker w = f.newWorker("hello");
        w.registerWorkflowImplementationTypes(HelloWorkflowImpl.class);
        f.start();
    }
}
```
Commands:
```bash
docker run --network=host --rm temporalio/tctl:0.21.1 workflow start --et 300 --tl hello --wt HelloWorkflow_getGreeting --input \"World\"
```

