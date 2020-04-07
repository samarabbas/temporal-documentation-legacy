# Installing Temporal Service and UI on a Mac

{% include youtubePlayer.html id="aLyRyNe5Ls0" %}

Commands executed during the tutorial:

```bash
docker-compose up

docker run --rm temporalio/tctl:latest --address host.docker.internal:7233 --namespace samples-namespace namespace register

docker run --rm temporalio/tctl:latest --address host.docker.internal:7233 --namespace samples-namespace namespace describe

alias tctl="docker run --rm temporalio/tctl:latest --address host.docker.internal:7233"

tctl --namespace samples-namespace namespace desc

tctl help

tctl workflow help

tctl --namespace samples-namespace workflow list

tctl --namespace samples-namespace workflow help start

tctl --namespace samples-namespace workflow start -wt test -tl test -et 300

tctl --namespace samples-namespace workflow list -op

tctl --namespace samples-namespace workflow terminate -wid <workflowId>

```
