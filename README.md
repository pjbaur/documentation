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
