# Getting Started

## Install Temporal Server Locally

### Install docker

Follow the Docker installation instructions found here: [https://docs.docker.com/engine/install](https://docs.docker.com/engine/install)

### Install docker-compose

Follow the docker-compose installation instructions found here: [https://docs.docker.com/compose/install](https://docs.docker.com/compose/install)

### Run Temporal Server Using docker-compose

Download the Temporal docker-compose file to preferred location (i.e. `quick_start` directory):
```bash
> curl -L https://github.com/temporalio/temporal/releases/download/v0.21.1/docker.tar.gz | tar -xz --strip-components 1 docker/docker-compose.yml
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   604  100   604    0     0   6357      0 --:--:-- --:--:-- --:--:--  6291
100  7294  100  7294    0     0  12909      0 --:--:-- --:--:-- --:--:-- 12909
> ls
docker-compose.yml
```

Start Temporal Service:
```bash
> docker-compose up
Creating network "quick_start_default" with the default driver
Pulling temporal (temporalio/temporal-auto-setup:0.21.1)...
latest: Pulling from temporalio/temporal-auto-setup
c9b1b535fdd9: Already exists
ab03e7ff4561: Pull complete
14fd2545310c: Pull complete
533daed3d2b9: Pull complete
b95a8eac833d: Pull complete
e1de77a2d35d: Pull complete
eaf3dbe1b068: Pull complete
bd5bc43b3fb4: Pull complete
eabe35b76c3c: Pull complete
ea376eb81229: Pull complete
703d31237512: Pull complete
dab4a595094e: Pull complete
9310c0f9d984: Pull complete
cc0bc9bd74b8: Pull complete
778edd6d0a46: Pull complete
af1b0ec58eda: Pull complete
4a5b2a88e880: Pull complete
Digest: sha256:3b71ffda90cd3016a764899cf2f43c9b3e3154643607f76382d5536658f2a885
Status: Downloaded newer image for temporalio/temporal-auto-setup:0.21.1
Creating quick_start_statsd_1    ... done
Creating quick_start_cassandra_1 ... done
Creating quick_start_temporal_1  ... done
Attaching to quick_start_cassandra_1, quick_start_statsd_1, quick_start_temporal_1
statsd_1     | Started runsvdir, PID is 39
statsd_1     | wait for processes to start....
cassandra_1  | CompilerOracle: inline org/apache/cassandra/io/util/Memory.checkBounds (JJ)V
cassandra_1  | CompilerOracle: inline org/apache/cassandra/io/util/SafeMemory.checkBounds (JJ)V
cassandra_1  | CompilerOracle: inline org/apache/cassandra/utils/AsymmetricOrdering.selectBoundary (Lorg/apache/cassandra/utils/AsymmetricOrdering/Op;II)I
cassandra_1  | CompilerOracle: inline org/apache/cassandra/utils/AsymmetricOrdering.strictnessOfLessThan (Lorg/apache/cassandra/utils/AsymmetricOrdering/Op;)I
cassandra_1  | CompilerOracle: inline org/apache/cassandra/utils/BloomFilter.indexes (Lorg/apache/cassandra/utils/IFilter/FilterKey;)[J
cassandra_1  | CompilerOracle: inline org/apache/cassandra/utils/BloomFilter.setIndexes (JJIJ[J)V
temporal_1   | + DB=cassandra
temporal_1   | + ENABLE_ES=false
temporal_1   | + ES_PORT=9200
temporal_1   | + RF=1
temporal_1   | + DEFAULT_NAMESPACE=default
temporal_1   | + DEFAULT_NAMESPACE_RETENTION=1
...
...
...
temporal_1   | + tctl --ns default namespace register --rd 1 --desc 'Default namespace for Temporal Server'
temporal_1   | Namespace default successfully registered.
temporal_1   | + tctl --ns default namespace describe
temporal_1   | Name: default
temporal_1   | UUID: 0d432509-d5ec-46e7-9fa2-f395b9ec6b26
temporal_1   | Description: Default namespace for Temporal Server
temporal_1   | OwnerEmail:
temporal_1   | NamespaceData: map[string]string(nil)
temporal_1   | Status: NamespaceStatusRegistered
temporal_1   | RetentionInDays: 1
temporal_1   | EmitMetrics: false
temporal_1   | ActiveClusterName: active
temporal_1   | Clusters: active
temporal_1   | HistoryArchivalStatus: ArchivalStatusEnabled
temporal_1   | HistoryArchivalURI: file:///tmp/temporal_archival/development
temporal_1   | VisibilityArchivalStatus: ArchivalStatusDisabled
temporal_1   | Bad binaries to reset:
temporal_1   | +-----------------+----------+------------+--------+
temporal_1   | | BINARY CHECKSUM | OPERATOR | START TIME | REASON |
temporal_1   | +-----------------+----------+------------+--------+
temporal_1   | +-----------------+----------+------------+--------+
temporal_1   | + echo 'Default namespace registration complete.'
temporal_1   | Default namespace registration complete.
```

Note that a default namespace is created upon first cluster start.

## Write Workflows and Activities using Client SDK

Try out [Java SDK](06_javaclient/01_quick_start#). 

Try out [Go SDK](07_goclient/001_quick_start#). 
