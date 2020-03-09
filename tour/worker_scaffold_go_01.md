---
codecontent: workerscaffoldgo01
weight: 20
categories: [tour]
---

# Building a Temporal Worker Scaffold in Go

The worker is responsible for running workflows and activities. It uses the Temporal client library 
to register with the Temporal server and poll for work. In this part of the tour, you'll build a 
worker using the Temporal Go client.

To install Go on Mac, use `brew install go`. Otherwise, follow the instructions from the 
[official site](http://golang.org/doc/install). Make sure that the **GOPATH** environment variable 
is set on your machine before proceeding.

Go projects should be under the **GOPATH** so use these commands to create a new folder for the 
worker.
