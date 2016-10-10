===================
Replication Choices
===================

Patroni uses Postgres' streaming replication, which is asynchronous by default. For more information, see the `Postgres documentation on streaming replication <http://www.postgresql.org/docs/current/static/warm-standby.html#STREAMING-REPLICATION>`__.

Patroni's asynchronous replication configuration allows for ``maximum_lag_on_failover`` settings. This setting ensures failover will not occur if a follower is more than a certain number of bytes behind the follower. This setting should be increased or decreased based on business requirements.

When asynchronous replication is not optimal for your use case, investigate Postgres's `synchronous replication <http://www.postgresql.org/docs/current/static/warm-standby.html#SYNCHRONOUS-REPLICATION>`__. Synchronous replication ensures consistency across a cluster by confirming that writes are written to a secondary before returning to the connecting client with a success. The cost of synchronous replication: reduced throughput on writes. This throughput will be entirely based on network performance.

In hosted datacenter environments (like AWS, Rackspace, or any network you do not control), synchronous replication significantly increases the variability of write performance. If followers become inaccessible from the leader, the leader effectively becomes read-only.

To enable a simple synchronous replication test, add the follow lines to the ``parameters`` section of your YAML configuration files:

.. code:: YAML

        synchronous_commit: "on"
        synchronous_standby_names: "*"

When using synchronous replication, use at least three Postgres data nodes to ensure write availability if one host fails.

Choosing your replication schema is dependent on your business considerations. Investigate both async and sync replication, as well as other HA solutions, to determine which solution is best for you.
