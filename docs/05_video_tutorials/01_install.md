# Installing Temporal Service and UI on a Mac

{% include youtubePlayer.html id="aLyRyNe5Ls0" %}

Commands executed during the tutorial:

```bash
docker-compose up

docker run --rm temporalio/tctl:latest --address host.docker.internal:7233 --domain samples-domain domain register

docker run --rm temporalio/tctl:latest --address host.docker.internal:7233 --domain samples-domain domain describe

alias tctl="docker run --rm temporalio/tctl:latest --address host.docker.internal:7233"

tctl --domain samples-domain domain desc

tctl help

tctl workflow help

tctl --domain samples-domain workflow list

tctl --domain samples-domain workflow help start

tctl --domain samples-domain workflow start -wt test -tl test -et 300

tctl --domain samples-domain workflow list -op

tctl --domain samples-domain workflow terminate -wid <workflowID>

```
