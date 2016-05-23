Parity Guide
============

Welcome to Parity Guide. The purpose of this document is to describe general
principles and practices for use and development of Parity projects.


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
