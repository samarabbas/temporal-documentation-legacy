---
codecontent: createsamplenamespace
weight: 15
categories: [tour]
---

# Create the Sample Namespace

All workflows and activities in Temporal run within a namespace. They need to be registered with the namespace before 
they can be used. Let's create the namespace that will be used for all the samples in this tour.

Note that you don't need to create the namespace every time you start the Temporal server. If you used *Ctrl+C* to 
shut down the server, the contents of the database remain intact. This means that when you start the server 
again with `docker-compose up`, the namespace will still be there. However, if you shut down the Temporal server 
with `docker-compose down`, that will wipe out the data and you'll need to create the namespace again.

## Using the CLI

The Temporal CLI can be used directly from the Docker image *temporalio/tctl* or by 
[building the CLI tool](https://github.com/temporalio/temporal/tree/master/tools/cli#how) locally (which requires 
cloning the server code). The samples in this tour will use the Docker image. If using a locally built 
version, replace `docker run --rm temporalio/tctl:0.21.1` with `tctl`.

## Environment variables

To keep the CLI commands short, we'll use some environment variables. These include the following:

- **TEMPORAL_CLI_ADDRESS** - host:port for Temporal frontend service, the default is for the local server
- **TEMPORAL_CLI_NAMESPACE** - default workflow namespace, so you don't need to specify `--namespace`
- **USER** - this is assigned by default in Linux/Mac but not on Windows
