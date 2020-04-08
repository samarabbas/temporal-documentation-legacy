# Worker Service

A worker or *worker service* is a service that hosts the workflow and activity implementations. The worker polls the *Temporal service* for tasks, performs those tasks, and communicates task execution results back to the *Temporal service*. Worker services are developed, deployed, and operated by Temporal customers.

You can run a Temporal worker in a new or an existing service. Use the framework APIs to start the Temporal worker and link in all activity and workflow implementations that you require the service to execute.

```go
package main

import (
	"os"
	"os/signal"

	"github.com/uber-go/tally"
	"go.uber.org/zap"

	"go.temporal.io/temporal/client"
	"go.temporal.io/temporal/worker"
	"go.temporal.io/temporal/workflow"
)

var (
	Tasklist  = "samples_tl"
)

func main() {
	logger, err := zap.NewDevelopment()
	if err != nil {
		panic(err)
	}

	// The client and worker are heavyweight objects that should be created once per process.
	serviceClient, err := client.NewClient(client.Options{
		HostPort: client.DefaultHostPort,
	})
	if err != nil {
		logger.Fatal("Unable to create client", zap.Error(err))
	}
	defer func() { _ = serviceClient.CloseConnection() }()

	worker := worker.New(serviceClient, Tasklist, worker.Options{
		Logger: logger,
	})

	worker.RegisterWorkflow(MyWorkflow)
	worker.RegisterActivity(MyActivity)

	err = worker.Start()
	if err != nil {
		logger.Fatal("Unable to start worker", zap.Error(err))
	}
	defer worker.Stop()

	// The workers are supposed to be long running process that should not exit.
	waitCtrlC()
}

func waitCtrlC() {
	ch := make(chan os.Signal, 1)
	signal.Notify(ch, os.Interrupt)
	<-ch
}

func MyWorkflow(context workflow.Context) error {
	return nil
}

func MyActivity() error {
	return nil
}
```
