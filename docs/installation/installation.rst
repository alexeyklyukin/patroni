============
Installation
============

**For Mac**

To install requirements on a Mac, run the following:

::

    brew install postgresql etcd haproxy libyaml python
    pip install psycopg2 pyyaml

=======
Running
=======

To get started, do the following from different terminals:
::

    > etcd --data-dir=data/etcd
    > ./patroni.py postgres0.yml
    > ./patroni.py postgres1.yml

You will then see a high-availability cluster start up. Test different settings in the YAML files to see how the cluster's behavior changes. Kill some of the components to see how the system behaves.

Add more ``postgres*.yml`` files to create an even larger cluster.

Patroni provides an `HAProxy <http://www.haproxy.org/>`__ configuration, which will give your application a single endpoint for connecting to the cluster's leader. To configure,
run:

::

    > haproxy -f haproxy.cfg

::

    > psql --host 127.0.0.1 --port 5000 postgres
