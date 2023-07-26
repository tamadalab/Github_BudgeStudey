|Linux/macOS|Linux i386|Windows|Coverity|Code Coverage|
|:---:|:---:|:---:|:---:|:---:|
|[![Build Status Linux/macOS](https://github.com/timescale/timescaledb/workflows/Regression/badge.svg?event=schedule)](https://github.com/timescale/timescaledb/actions?query=workflow%3ARegression+branch%3Amain)|[![Build Status Linux i386](https://github.com/timescale/timescaledb/workflows/Regression%20Linux%20i386/badge.svg?branch=main&event=schedule)](https://github.com/timescale/timescaledb/actions?query=workflow%3A%22Regression+Linux+i386%22+branch%3Amain)|[![Windows build status](https://github.com/timescale/timescaledb/workflows/Regression%20Windows/badge.svg?branch=main&event=schedule)](https://github.com/timescale/timescaledb/actions?query=workflow%3A%22Regression+Windows%22+branch%3Amain)|[![Coverity Scan Build Status](https://scan.coverity.com/projects/timescale-timescaledb/badge.svg)](https://scan.coverity.com/projects/timescale-timescaledb)|[![Code Coverage](https://codecov.io/gh/timescale/timescaledb/branch/main/graphs/badge.svg?branch=main)](https://codecov.io/gh/timescale/timescaledb)


## TimescaleDB

TimescaleDB is an open-source database designed to make SQL scalable for
time-series data.  It is engineered up from PostgreSQL and packaged as a
PostgreSQL extension, providing automatic partitioning across time and space
(partitioning key), as well as full SQL support.

If you prefer not to install or administer your instance of [TimescaleDB](https://tsdb.co/GitHubTimescale),
try Timescale, our fully managed cloud offering (pay-as-you-go, with a free trial to start).

To determine which option is best for you, see [Timescale Products](https://tsdb.co/GitHubTimescaleProducts)
for more information about our Apache-2 version, TimescaleDB Community (self-hosted), and Timescale 
Cloud (hosted), including: feature comparisons, FAQ, documentation, and support.

Below is an introduction to TimescaleDB. For more information, please check out 
these other resources:
- [Developer Documentation](https://tsdb.co/GitHubTimescaleDocs)
- [Slack Channel](https://slack-login.timescale.com)
- [Timescale Community Forum](https://www.timescale.com/forum/)
- [Timescale Release Notes & Future Plans](https://tsdb.co/GitHubTimescaleReleaseNotes)

For reference and clarity, all code files in this repository reference
licensing in their header (either the Apache-2-open-source license
or [Timescale License (TSL)](https://github.com/timescale/timescaledb/blob/main/tsl/LICENSE-TIMESCALE)
). Apache-2 licensed binaries can be built by passing `-DAPACHE_ONLY=1` to `bootstrap`.

[Contributors welcome.](https://github.com/timescale/timescaledb/blob/main/CONTRIBUTING.md)

(To build TimescaleDB from source, see instructions in [_Building from source_](https://github.com/timescale/timescaledb/blob/main/docs/BuildSource.md).)

### Using TimescaleDB

TimescaleDB scales PostgreSQL for time-series data via automatic
partitioning across time and space (partitioning key), yet retains
the standard PostgreSQL interface.

In other words, TimescaleDB exposes what look like regular tables, but
are actually only an
abstraction (or a virtual view) of many individual tables comprising the
actual data. This single-table view, which we call a
[hypertable](https://tsdb.co/GitHubTimescaleHypertable),
is comprised of many chunks, which are created by partitioning
the hypertable's data in either one or two dimensions: by a time
interval, and by an (optional) "partition key" such as
device id, location, user id, etc. ([Architecture discussion](https://docs.timescale.com/timescaledb/latest/overview/core-concepts/))

Virtually all user interactions with TimescaleDB are with
hypertables. Creating tables and indexes, altering tables, inserting
data, selecting data, etc., can (and should) all be executed on the
hypertable.

From the perspective of both use and management, TimescaleDB just
looks and feels like PostgreSQL, and can be managed and queried as
such.

#### Before you start

PostgreSQL's out-of-the-box settings are typically too conservative for modern
servers and TimescaleDB. You should make sure your `postgresql.conf`
settings are tuned, either by using [timescaledb-tune](https://github.com/timescale/timescaledb-tune) 
or doing it manually.

#### Creating a hypertable

```sql
-- Do not forget to create timescaledb extension
CREATE EXTENSION timescaledb;

-- We start by creating a regular SQL table
CREATE TABLE conditions (
  time        TIMESTAMPTZ       NOT NULL,
  location    TEXT              NOT NULL,
  temperature DOUBLE PRECISION  NULL,
  humidity    DOUBLE PRECISION  NULL
);

-- Then we convert it into a hypertable that is partitioned by time
SELECT create_hypertable('conditions', 'time');
```

- [Quick start: Creating hypertables](https://tsdb.co/GitHubTimescaleCreateHypertables)
- [Reference examples](https://tsdb.co/GitHubTimescaleHypertableReference)

#### Inserting and querying data

Inserting data into the hypertable is done via normal SQL commands:

```sql
INSERT INTO conditions(time, location, temperature, humidity)
  VALUES (NOW(), 'office', 70.0, 50.0);

SELECT * FROM conditions ORDER BY time DESC LIMIT 100;

SELECT time_bucket('15 minutes', time) AS fifteen_min,
    location, COUNT(*),
    MAX(temperature) AS max_temp,
    MAX(humidity) AS max_hum
  FROM conditions
  WHERE time > NOW() - interval '3 hours'
  GROUP BY fifteen_min, location
  ORDER BY fifteen_min DESC, max_temp DESC;
```

In addition, TimescaleDB includes additional functions for time-series
analysis that are not present in vanilla PostgreSQL. (For example, the `time_bucket` function above.)

- [Quick start: Basic operations](https://tsdb.co/GitHubTimescaleBasicOperations)
- [Reference examples](https://tsdb.co/GitHubTimescaleWriteData)
- [TimescaleDB API](https://tsdb.co/GitHubTimescaleAPI)

### Installation

TimescaleDB is available pre-packaged for several platforms (Linux, Docker, MacOS, Windows).
More information can be found in [our documentation](https://docs.timescale.com/self-hosted/latest/install/).

To build from source, see instructions
[here](https://github.com/timescale/timescaledb/blob/main/docs/BuildSource.md).

[Timescale](https://tsdb.co/GitHubTimescale), a fully managed TimescaleDB in the cloud, is
available via a free trial. Create a PostgreSQL database in the cloud with TimescaleDB pre-installed
so you can power your application with TimescaleDB without the management overhead.

## Resources

### Architecture documents

- [Basic TimescaleDB Features](tsl/README.md)
- [Advanced TimescaleDB Features](tsl/README.md)
- [Testing TimescaleDB](test/README.md)

### Useful tools

- [timescaledb-tune](https://github.com/timescale/timescaledb-tune): Helps
set your PostgreSQL configuration settings based on your system's resources.
- [timescaledb-parallel-copy](https://github.com/timescale/timescaledb-parallel-copy):
Parallelize your initial bulk loading by using PostgreSQL's `COPY` across
multiple workers.

### Additional documentation

- [Why use TimescaleDB?](https://tsdb.co/GitHubTimescaleIntro)
- [Migrating from PostgreSQL](https://tsdb.co/GitHubTimescalePostgresMigrate)
- [Writing data](https://tsdb.co/GitHubTimescaleWriteData)
- [Querying and data analytics](https://tsdb.co/GitHubTimescaleReadData)
- [Tutorials and sample data](https://tsdb.co/GitHubTimescaleTutorials)

### Community & help

- [Slack Channel](https://slack.timescale.com)
- [Github Issues](https://github.com/timescale/timescaledb/issues)
- [Timescale Support](https://tsdb.co/GitHubTimescaleSupport): see support options (community & subscription)

### Releases & updates

 - [Timescale Release Notes & Future Plans](https://tsdb.co/GitHubTimescaleReleaseNotes): see planned and
   in-progress updates and detailed information about current and past
   releases. - [Subscribe to Timescale Release
   Notes](https://tsdb.co/GitHubTimescaleGetReleaseNotes) to get
   notified about new releases, fixes, and early access/beta programs.

### Contributing

- [Contributor instructions](https://github.com/timescale/timescaledb/blob/main/CONTRIBUTING.md)
- [Code style guide](https://github.com/timescale/timescaledb/blob/main/docs/StyleGuide.md)

