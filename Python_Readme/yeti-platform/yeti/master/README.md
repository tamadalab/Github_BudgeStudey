# Yeti - Your everyday threat intelligence

* [What is Yeti?](#what-is-yeti)
* [Installation](#installation)
* [Useful links](#useful-links)

## What is Yeti?

Yeti is a platform meant to organize observables, indicators of compromise,
TTPs, and knowledge on threats in a single, unified repository. Yeti will also
automatically enrich observables (e.g. resolve domains, geolocate IPs) so that
you don't have to. Yeti provides an interface for humans (shiny Bootstrap-based
UI) and one for machines (web API) so that your other tools can talk nicely to
it.

Yeti was born out of frustration of having to answer the question "where have
I seen this artifact before?" or Googling shady domains to tie them to a
malware family.

In a nutshell, Yeti allows you to:

* Submit observables and get a pretty good guess on the nature of the threat.
* Inversely, focus on a threat and quickly list all TTPs, Observables, and
  associated malware.
* Let responders skip the "Google the artifact" stage of incident response.
* Let analysts focus on adding intelligence rather than worrying about
  machine-readable export formats.
* Visualize relationship graphs between different threats.

This is done by:

* Collecting and processing observables from a wide array of different sources
  (MISP instances, malware trackers, XML feeds, JSON feeds...)
* Providing a web API to automate queries (think incident management platform)
  and enrichment (think malware sandbox).
* Export the data in user-defined formats so that they can be ingested by
  third-party applications (think blocklists, SIEM).

## Installation

Yeti has a `docker-compose` script to get up and running even faster; this is useful for testing or even running production instances of Yeti should your infrastructure support it. Full instructions [here](https://github.com/yeti-platform/yeti/tree/master/extras/docker), but in a nutshell:

Download in release page the lastest version of yeti <https://github.com/yeti-platform/yeti/releases>

To install docker and docker-compose follow the instructions on the official documentation <https://docs.docker.com/compose/install/>

```bash
    gunzip yeti-<version>.zip
    cd yeti/extras/docker/dev
    docker-compose up
```

The docker-compose will start the following containers

## Useful links

* [Documentation](http://yeti-platform.readthedocs.io/en/latest/)
* [Yeti users mailing list](https://groups.google.com/forum/#!forum/yeti-users)
* [Project website & blog](https://yeti-platform.github.io)
* [Installation](http://yeti-platform.readthedocs.io/en/latest/installation.html)
* [Use-cases](https://yeti-platform.readthedocs.io/en/latest/use-cases.html)
