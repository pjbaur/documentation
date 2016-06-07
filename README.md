Parity Guide
============

Welcome to Parity Guide. The purpose of this document is to describe general
principles and practices for use and development of Parity projects.


Introduction
------------

This section gives an introduction to Parity projects.


### Overview

Parity projects implement components for trading infrastructure. They have two
focus areas:

  - The **market connectivity** libraries enable applications on the Java
    Virtual Machine (JVM) to connect to trading venues and brokerage firms.

  - The **trading system** applications provide a software platform for
    running a trading venue.

The following projects focus on market connectivity:

  - **[Foundation][]** contains building blocks for implementing network
    protocols. These include routines for manipulating, for example, ASCII
    strings and byte arrays.

  - **[Nassau][]** implements NASDAQ transport protocols. These provide
    reliable transport for delimited, sequenced messages either between two
    endpoints or from one sender to many receivers. Nassau depends on
    Foundation.

  - **[Juncture][]** implements connectivity to various trading venues using
    their proprietary market data and order entry protocols. It can be used
    for both live market access and historical market data analysis. It
    depends on Foundation and, for connectivity to NASDAQ, Nassau.

  - **[Philadelphia][]** is a Financial Information Exchange (FIX) engine. It
    implements the standard protocol versions from FIX 4.2 to FIX 5.0 Service
    Pack 2.

  - **[Philadelphia Extras][]** contains additional FIX dialects for
    Philadelphia. These augment the standard protocol versions with user
    defined tags, enumerations, and message types used by various trading
    venues.

  [Foundation]: https://github.com/paritytrading/foundation
  [Nassau]: https://github.com/paritytrading/nassau
  [Juncture]: https://github.com/paritytrading/juncture
  [Philadelphia]: https://github.com/paritytrading/philadelphia
  [Philadelphia Extras]: https://github.com/paritytrading/philadelphia-extras

The following projects are related to the trading system:

  - **[Parity][]** contains the core components of the trading system, such as
    the matching engine and the order entry and market data protocols. These
    are built on Foundation, Nassau, and Philadelphia.

  - **[Parity Extras][]** provides additional applications, such as a market
    event simulator, for the trading system. These interact with the trading
    system the same way market participants do, using the order entry and
    market data protocols.

  [Parity]: https://github.com/paritytrading/parity
  [Parity Extras]: https://github.com/paritytrading/parity-extras


Development
-----------

This section describes development of Parity projects.


### Test

Run the tests with Maven:

    mvn test


### Build

Build the artifacts with Maven:

    mvn package

Maven puts the artifacts into a `target` directory under each module.


### Run

After building the artifacts, the executables can be found in the `target`
directories. Their filenames have the following format:

    <module>-<version>.jar

Run an executable with Java:

    java -jar <executable>

If an executable requires a configuration file, an example of one can be found
as `devel.conf` in the `etc` directory under the module.


### Release

Follow these steps to publish a Maven project release:

  1. Update release notes.

  2. Prepare a release:

        mvn release:clean release:prepare

  3. Perform the release:

        mvn release:perform

  4. Log into [Sonatype OSSRH](http://oss.sonatype.org/).

  5. _Close_ the repository on Sonatype OSSRH.

  6. _Release_ the repository on Sonatype OSSRH.

  7. Update [API documentation](http://github.com/paritytrading/api).
