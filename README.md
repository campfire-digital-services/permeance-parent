<!--
This file is part of permeance-parent.

permeance-parent is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your option) any
later version.

permeance-parent is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with
permeance-parent. If not, see <http://www.gnu.org/licenses/>.
-->
Introduction
============

This module provides a [maven](http://maven.apache.org) parent-pom which can be used to defined artifacts which employ
a couple of very useful maven configurations. Out of the box, you get:

  + A [maven-enforcer-plugin](http://maven.apache.org/plugins/maven-enforcer-plugin) configuration which will require
    proper dependency management.

  + A [maven-compiler-plugin](http://maven.apache.org/plugins/maven-compiler-plugin) configuration for java 6, but
    which will be noisy with warnings so you can fix them.

  + Several [maven profiles](http://maven.apache.org/guides/introduction/introduction-to-profiles.html):

    + 'paranoid' which enables additional build time checks using the plugins:

      + [maven-checkstyle-plugin](http://maven.apache.org/plugins/maven-checkstyle-plugin/) for checking source code
        metrics against the rules defined in
        [permeance-checkstyle.xml](https://raw.github.com/permeance/permeance-parent/master/permeance-checkstyle.xml).

      + [maven-pmd-plugin](http://maven.apache.org/plugins/maven-pmd-plugin/) for checking byte code metrics against
        the rules defined in
        [permeance-pmd.xml](https://raw.github.com/permeance/permeance-parent/master/permeance-pmd.xml)

      + [cobertura-maven-plugin](http://mojo.codehaus.org/cobertura-maven-plugin/) for verifying unit test coverage of
        atleast 75% across all lines and branches across all classes, packages and modules.

      + [findbugs-maven-plugin](http://mojo.codehaus.org/findbugs-maven-plugin/) for static byte code analysis to
        locate probable bugs.

      + [javancss-maven-plugin](http://mojo.codehaus.org/javancss-maven-plugin/) for checking of various source metrics
        such as size and complexity.

    + 'documented' which enables project site generation via the [maven-site-plugin]() with the reports:

      + [maven-changelog-plugin](http://maven.apache.org/plugins/maven-changelog-plugin/) for reporting SCM changes.

      + [maven-dependency-plugin](http://maven.apache.org/plugins/maven-dependency-plugin/) for summarising dependency
        information.

      + [maven-javadoc-plugin](http://maven.apache.org/plugins/maven-javadoc-plugin/) for incorporating generated
        javadocs from project source within the site.

      + [maven-jxr-plugin](http://maven.apache.org/plugins/maven-jxr-plugin/) for incorporating java source cross
        reference within the site.

      + [maven-linkcheck-plugin](http://maven.apache.org/plugins/maven-linkcheck-plugin/) for checking generated html
        links within project reports.

      + [maven-project-info-reports-plugin](http://maven.apache.org/plugins/maven-project-info-reports-plugin/) for
        generating miscellaneous reports on project information.

      + [maven-surefire-report-plugin](http://maven.apache.org/plugins/maven-surefire-report-plugin/) for reporting
        on unit test outcomes.

      + [jdepend-maven-plugin](http://mojo.codehaus.org/jdepend-maven-plugin/) for generating package and class
        dependency reports.

      + [license-maven-plugin](http://mojo.codehaus.org/license-maven-plugin/) for reporting on the licenses used by
        project dependencies.

      + [taglist-maven-plugin](http://mojo.codehaus.org/taglist-maven-plugin/) for reporting on TODO's within project
        source code.

      + [versions-maven-plugin](http://mojo.codehaus.org/versions-maven-plugin/) for reporting on dependency and plugin
        version statuses.

    + 'paranoid+documented' which enables additional information in site generation based on the 'paranoid' profile:

      + [maven-pmd-plugin](http://maven.apache.org/plugins/maven-pmd-plugin/) for reporting on PMD checks and
        violations found during execution of the 'paranoid' profile.

      + [maven-checkstyle-plugin](http://maven.apache.org/plugins/maven-checkstyle-plugin/) for reporting on checkstyle
        violations found during execution of the 'paranoid' profile.

      + [findbugs-maven-plugin](http://mojo.codehaus.org/findbugs-maven-plugin/) for reporting on findbugs violations
        found during execution of the 'paranoid' profile.

      + [cobertura-maven-plugin](http://mojo.codehaus.org/cobertura-maven-plugin/) for reporting on cobertura
        violations found during the execution of the 'paranoid' profile.

      + [javancss-maven-plugin](http://mojo.codehaus.org/javancss-maven-plugin/) for reporting on JavaNCSS violations
        found during the execution of the 'paranoid' profile.

Usage
=====

Until this artifact is hosted somewhere centrally, you'll need to check it out, and install it locally via the standard
"mvn install" command. Something like:

```shell
$ mvn install
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building permeance-parent 0.1-SNAPSHOT
[INFO] ------------------------------------------------------------------------
...
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 2.742s
[INFO] Finished at: Mon May 21 21:21:52 EST 2012
[INFO] Final Memory: 4M/81M
[INFO] ------------------------------------------------------------------------
```

Once that is done, you can then use this module's artifacts as the parent coordinates for your project:

```xml
<parent>
     <groupId>au.com.permeance</groupId>
     <artifactId>permeance-parent</artifactId>
     <version>0.1-SNAPSHOT</version>
 </parent>
```

License
=======

This project is licensed under the
[GNU Lesser General Public License, Version 3](http://www.gnu.org/licenses/lgpl-3.0.html)
