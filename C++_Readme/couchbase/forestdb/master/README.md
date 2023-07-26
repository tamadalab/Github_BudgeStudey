# ForestDB

ForestDB is a key-value storage engine developed by Couchbase Caching and Storage Team, and its main index structure is built from [Hierarchical B+-Tree based Trie](http://db.csail.mit.edu/sigmod11contest/sigmod_2011_contest_poster_jungsang_ahn.pdf), called HB+-Trie. [ForestDB paper](https://www.computer.org/csdl/trans/tc/preprint/07110563.pdf) has been published in IEEE Transactions on Computers.

Compared with traditional B+-Tree based storage engines, ForestDB shows significantly better read and write performance with less storage overhead. ForestDB has been tested on various server OS environments (Centos, Ubuntu, Mac OS x, Windows) and mobile OSs (iOS, Android). The test coverage stats for ForestDB are available in [ForestDB Code Coverage Report](http://labs.couchbase.com/fdbcoverage/index.html).

[ForestDB benchmark program](https://github.com/couchbaselabs/ForestDB-Benchmark) is also available for performance comparisons with other key-value storage engines.

Please visit the [ForestDB wiki](https://github.com/couchbaselabs/forestdb/wiki) for more details.

## Main Features

- Keys and values are treated as an arbitrary binary.
- Applications can supply a custom compare function to support a customized key order.
- A value can be retrieved by its sequence number or disk offset in addition to a key.
- Write-Ahead Logging (WAL) and its in-memory index are used to reduce the main index lookup / update overhead.
- Multi-Version Concurrency Control (MVCC) support and append-only storage layer.
- Multiple snapshot instances can be created from a given ForestDB instance to provide different views of database.
- Rollback is supported to revert the database to a specific point.
- Ranged iteration by keys or sequence numbers is supported for a partial or full range lookup operation.
- Manual or auto compaction can be configured per ForestDB database file.
- Transactional support with read\_committed or read\_uncommitted isolation level.

## How to build

See INSTALL.MD

## How to Use

Please refer to [Public APIs](https://github.com/couchbaselabs/forestdb/wiki/Public-APIs) and tests/fdb\_functional\_test.cc in ForestDB source directory.

## How to contribute code

1. Sign the [Couchbase Contributor License
Agreement](http://review.couchbase.org/static/individual_agreement.html)
1. Submit code changes via either a Github PR or via Gerrit (for Gerrit usage, see [Instructions](https://github.com/couchbase/couchbase-spark-connector/blob/master/CONTRIBUTING.md#preparing-for-contribution) from the couchbase-spark-connector project.)

# Note regarding master branch
The 'master' git branch of forestdb contains a number of changes which ultimately were not kept for production builds of Couchbase Server. Production builds were kept on an earlier release branch named 'watson' corresponding to Couchbase Server 4.5. Couchbase Server 5.0, 5.1, 5.5, and 6.0 added some bug fixes on branches made from 'watson', namely 'spock' and 'vulcan'. For Couchbase Server 6.5 and forward, a new branch 'cb-master' was created from the then-current 'vulcan' branch.

'cb-master' should be seen as the equivalent of 'master' for all Couchbase Server production build purposes. Any additional production bug fixes will go there, and release-specific branches will be made from there when necessary.

The current 'master' branch is left untouched and unsupported, for use by community users who may depend on the work done there.
