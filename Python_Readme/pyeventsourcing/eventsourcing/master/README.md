[![Build Status](https://github.com/pyeventsourcing/eventsourcing/actions/workflows/runtests.yaml/badge.svg?branch=main)](https://github.com/pyeventsourcing/eventsourcing/tree/main)
[![Coverage Status](https://coveralls.io/repos/github/pyeventsourcing/eventsourcing/badge.svg?branch=main)](https://coveralls.io/github/pyeventsourcing/eventsourcing?branch=main)
[![Documentation Status](https://readthedocs.org/projects/eventsourcing/badge/?version=stable)](https://eventsourcing.readthedocs.io/en/stable/)
[![Latest Release](https://badge.fury.io/py/eventsourcing.svg)](https://pypi.org/project/eventsourcing/)
[![Downloads](https://static.pepy.tech/personalized-badge/eventsourcing?period=total&units=international_system&left_color=grey&right_color=brightgreen&left_text=downloads)](https://pypistats.org/packages/eventsourcing)
[![Code Style: Black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)


# Event Sourcing in Python

A library for event sourcing in Python.

*"totally amazing and a pleasure to use"*

*"very clean and intuitive"*

*"a huge help and time saver"*

Please [read the docs](https://eventsourcing.readthedocs.io/). See also [extension projects](https://github.com/pyeventsourcing).


## Installation

Use pip to install the [stable distribution](https://pypi.org/project/eventsourcing/)
from the Python Package Index.

    $ pip install eventsourcing

Please note, it is recommended to install Python
packages into a Python virtual environment.


## Synopsis

Define aggregates with the `Aggregate` class and the `@event` decorator.

```python
from eventsourcing.domain import Aggregate, event

class Dog(Aggregate):
    @event('Registered')
    def __init__(self, name):
        self.name = name
        self.tricks = []

    @event('TrickAdded')
    def add_trick(self, trick):
        self.tricks.append(trick)
```

Define application objects with the `Application` class.

```python
from eventsourcing.application import Application

class DogSchool(Application):
    def register_dog(self, name):
        dog = Dog(name)
        self.save(dog)
        return dog.id

    def add_trick(self, dog_id, trick):
        dog = self.repository.get(dog_id)
        dog.add_trick(trick)
        self.save(dog)

    def get_dog(self, dog_id):
        dog = self.repository.get(dog_id)
        return {'name': dog.name, 'tricks': tuple(dog.tricks)}
```

Write a test.

```python
def test_dog_school():
    # Construct application object.
    school = DogSchool()

    # Evolve application state.
    dog_id = school.register_dog('Fido')
    school.add_trick(dog_id, 'roll over')
    school.add_trick(dog_id, 'play dead')

    # Query application state.
    dog = school.get_dog(dog_id)
    assert dog['name'] == 'Fido'
    assert dog['tricks'] == ('roll over', 'play dead')

    # Select notifications.
    notifications = school.notification_log.select(start=1, limit=10)
    assert len(notifications) == 3
```

Run the test with the default persistence module. Events are stored
in memory using Python objects.

```python
test_dog_school()
```

Configure the application to run with an SQLite database. Other persistence modules are available.

```python
import os

os.environ["PERSISTENCE_MODULE"] = 'eventsourcing.sqlite'
os.environ["SQLITE_DBNAME"] = 'dog-school.db'
```

Run the test with SQLite.

```python
test_dog_school()
```

See the [documentation](https://eventsourcing.readthedocs.io/) for more information.


## Features

**Aggregates and applications** — base classes for event-sourced aggregates
and applications. Suggests how to structure an event-sourced application. All
classes are fully type-hinted to guide developers in using the library.

**Flexible event store** — flexible persistence of aggregate events. Combines
an event mapper and an event recorder in ways that can be easily extended.
Mapper uses a transcoder that can be easily extended to support custom
model object types. Recorders supporting different databases can be easily
substituted and configured with environment variables.

**Application-level encryption and compression** — encrypts and decrypts events inside the
application. This means data will be encrypted in transit across a network ("on the wire")
and at disk level including backups ("at rest"), which is a legal requirement in some
jurisdictions when dealing with personally identifiable information (PII) for example
the EU's GDPR. Compression reduces the size of stored aggregate events and snapshots, usually
by around 25% to 50% of the original size. Compression reduces the size of data
in the database and decreases transit time across a network.

**Snapshotting** — reduces access-time for aggregates that have many events.

**Versioning** - allows changes to be introduced after an application
has been deployed. Both aggregate events and aggregate snapshots can be versioned.

**Optimistic concurrency control** — ensures a distributed or horizontally scaled
application doesn't become inconsistent due to concurrent method execution. Leverages
optimistic concurrency controls in adapted database management systems.

**Notifications and projections** — reliable propagation of application
events with pull-based notifications allows the application state to be
projected accurately into replicas, indexes, view models, and other applications.
Supports materialized views and CQRS.

**Event-driven systems** — reliable event processing. Event-driven systems
can be defined independently of particular persistence infrastructure and mode of
running.

**Detailed documentation** — documentation provides general overview, introduction
of concepts, explanation of usage, and detailed descriptions of library classes.
All code is annotated with type hints.

**Worked examples** — includes examples showing how to develop aggregates, applications
and systems.


## Extensions

The GitHub organisation
[Event Sourcing in Python](https://github.com/pyeventsourcing)
hosts extension projects for the Python eventsourcing library.
There are projects that adapt popular ORMs such as
[Django](https://github.com/pyeventsourcing/eventsourcing-django)
and [SQLAlchemy](https://github.com/pyeventsourcing/eventsourcing-sqlalchemy).
There are projects that adapt specialist event stores such as
[Axon Server](https://github.com/pyeventsourcing/eventsourcing-axonserver),
[EventStoreDB](https://github.com/pyeventsourcing/eventsourcing-eventstoredb).
There are projects that support popular NoSQL databases such as
[DynamoDB](https://github.com/pyeventsourcing/eventsourcing-dynamodb)
and MongoDB.
There are also projects that provide examples of using the
library with web frameworks as
[FastAPI](https://github.com/pyeventsourcing/example-fastapi)
and [Flask](https://github.com/pyeventsourcing/example-flask).
And there are examples of event-sourced applications and systems
of event-sourced applications, such as the
[Paxos system](https://github.com/pyeventsourcing/example-paxos),
which is used as the basis for a
[replicated state machine](https://github.com/pyeventsourcing/example-paxos/tree/master/replicatedstatemachine),
which is used as the basis for a
[distributed key-value store](https://github.com/pyeventsourcing/example-paxos/tree/master/keyvaluestore).

## Project

This project is [hosted on GitHub](https://github.com/pyeventsourcing/eventsourcing).

Please register questions, requests and
[issues on GitHub](https://github.com/pyeventsourcing/eventsourcing/issues),
or post in the project's Slack channel.

There is a [Slack channel](https://join.slack.com/t/eventsourcinginpython/shared_invite/enQtMjczNTc2MzcxNDI0LTJjMmJjYTc3ODQ3M2YwOTMwMDJlODJkMjk3ZmE1MGYyZDM4MjIxODZmYmVkZmJkODRhZDg5N2MwZjk1YzU3NmY)
for this project, which you are [welcome to join](https://join.slack.com/t/eventsourcinginpython/shared_invite/enQtMjczNTc2MzcxNDI0LTJjMmJjYTc3ODQ3M2YwOTMwMDJlODJkMjk3ZmE1MGYyZDM4MjIxODZmYmVkZmJkODRhZDg5N2MwZjk1YzU3NmY).

Please refer to the [documentation](https://eventsourcing.readthedocs.io/) for installation and usage guides.
