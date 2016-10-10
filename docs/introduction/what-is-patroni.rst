===============
What is Patroni
===============

Patroni is a template for you to create your own customized, high-availability solution using Python and - for maximum
accessibility - a distributed configuration store like `ZooKeeper <https://zookeeper.apache.org/>`__, `etcd
<https://github.com/coreos/etcd>`__ or `Consul <https://github.com/hashicorp/consul>`__. Database engineers, DBAs, DevOps
engineers, and SREs who are looking to quickly deploy HA PostgreSQL in the datacenter-or anywhere else-will hopefully find it
useful.

We call Patroni a "template" because it is far from being a one-size-fits-all or plug-and-play replication system. It will
have its own caveats. Use wisely.

**Note to Kubernetes users: We're currently developing Patroni to be as useful as possible for teams running Kubernetes on
**top of Google Compute Engine; Patroni can be the HA solution for Postgres in such an environment. Please contact us via our
**Issues Tracker if this describes your team's current setup, and we'll follow up.

Patroni originated as a fork of `Governor <https://github.com/compose/governor>`__, the project from Compose. It includes
plenty of new features.

There are many ways to run high availability with PostgreSQL; for a list, see the `PostgreSQL Documentation
<https://wiki.postgresql.org/wiki/Replication,_Clustering,_and_Connection_Pooling>`__.

