Overview
========

This project illustrates how to integrate the following quality assurance tools with [Play](http://www.playframework.com/) applications:

  * [PMD](http://pmd.sourceforge.net/) source code analysis
  * [Checkstyle](http://checkstyle.sourceforge.net/) source code analysis
  * [FindBugs](http://findbugs.sourceforge.net/) byte code analysis
  * [JavaDoc](http://www.oracle.com/technetwork/java/javase/documentation/index-jsp-135444.html) and [ScalaDoc](http://docs.scala-lang.org/style/scaladoc.html) documentation generation
  * [Jacoco](http://www.eclemma.org/jacoco/) test coverage analysis

Installation
============

Adding these tools to your Play project requires changes to the [project/](https://github.com/ics-software-engineering/play-example-quality-assurance/tree/master/project) directory:

  * Update [plugins.sbt](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/plugins.sbt) to add libraries.
  * Update [Build.scala](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/Build.scala) to add commands to the play console.
  * Add command definition files: [ApiDocSettings.scala](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/ApiDocSettings.scala), [CheckstyleSettings.scala](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/CheckstyleSettings.scala), and [PmdSettings.scala](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/PmdSettings.scala).
  * Add (and maybe modify) configuration files: [checkstyle-config.xml](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/checkstyle-config.xml), [pmd-ruleset.xml](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/pmd-ruleset.xml), and [findbugs-excludefilter.xml](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/findbugs-excludefilter.xml).
  
Screencast
==========

Click the image below to watch a 14 minute walkthrough of this example:

[<img src="https://raw.github.com/ics-software-engineering/play-example-quality-assurance/master/doc/play-example-quality-assurance-screenshot.png" width="400">](https://www.youtube.com/watch?v=uRknW9EjISw)  
  

Example invocations
===================

PMD
---

```
[~/projecthosting/github/play-example-quality-assurance]-> play pmd
[info] Loading project definition from /Users/johnson/projecthosting/github/play-example-quality-assurance/project
[info] Set current project to play-example-quality-assurance (in build file:/Users/johnson/projecthosting/github/play-example-quality-assurance/)
[info] Running PMD...
[info] 
[success] Total time: 1 s, completed Jun 10, 2013 1:33:54 PM
```

The output file is in target/pmd/pmd-report.txt and echoed to the console.  For Play's default application, no PMD warnings are generated, resulting in a blank info line output.

Modify [pmd-ruleset.xml](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/pmd-ruleset.xml) to change the way PMD analyzes your code. 

Checkstyle
----------

```
[~/projecthosting/github/play-example-quality-assurance]-> play checkstyle
[info] Loading project definition from /Users/johnson/projecthosting/github/play-example-quality-assurance/project
[info] Set current project to play-example-quality-assurance (in build file:/Users/johnson/projecthosting/github/play-example-quality-assurance/)
[info] Running checkstyle...
[info] Starting audit...
[info] /Users/johnson/projecthosting/github/play-example-quality-assurance/app/controllers/Application.java:0: Missing package-info.java file.
[info] /Users/johnson/projecthosting/github/play-example-quality-assurance/app/controllers/Application.java:3: Using the '.*' form of import should be avoided - play.*.
[info] /Users/johnson/projecthosting/github/play-example-quality-assurance/app/controllers/Application.java:4: Using the '.*' form of import should be avoided - play.mvc.*.
[info] /Users/johnson/projecthosting/github/play-example-quality-assurance/app/controllers/Application.java:6: Using the '.*' form of import should be avoided - views.html.*.
[info] /Users/johnson/projecthosting/github/play-example-quality-assurance/app/controllers/Application.java:8: Missing a Javadoc comment.
[info] /Users/johnson/projecthosting/github/play-example-quality-assurance/app/controllers/Application.java:9: Line has trailing spaces.
[info] /Users/johnson/projecthosting/github/play-example-quality-assurance/app/controllers/Application.java:10:5: Missing a Javadoc comment.
[info] /Users/johnson/projecthosting/github/play-example-quality-assurance/app/controllers/Application.java:13: Line has trailing spaces.
[info] /Users/johnson/projecthosting/github/play-example-quality-assurance/app/views/index.scala.html:4: Line has trailing spaces.
[info] /Users/johnson/projecthosting/github/play-example-quality-assurance/app/views/index.scala.html:6: Line has trailing spaces.
[info] Audit done.
[success] Total time: 1 s, completed Jun 10, 2013 1:39:55 PM
```

The output file is in target/checkstyle/checkstyle-report.txt and also echoed to the console. For Play's default application, 10 Checkstyle warnings are generated.

Modify [checkstyle-config.xml](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/checkstyle-config.xml) to change the way Checkstyle analyzes your code.

FindBugs
--------

```
[~/projecthosting/github/play-example-quality-assurance]-> play findbugs
[info] Loading project definition from /Users/johnson/projecthosting/github/play-example-quality-assurance/project
[info] Set current project to play-example-quality-assurance (in build file:/Users/johnson/projecthosting/github/play-example-quality-assurance/)
[success] Total time: 7 s, completed Jun 10, 2013 1:45:10 PM
```

The output file is in target/findbugs/findbugs.xml.  For Play's default application, no FindBug errors are generated, but the plugin will output the number of warnings found if non-zero.

Modify [findbugs-excludefilter.xml](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/findbugs-excludefilter.xml) to change the way findbugs processes your code. 
Additional FindBugs configuration options can be provided in [Build.scala](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/Build.scala).

Jacoco
------

```
[~/projecthosting/github/play-example-quality-assurance]-> play jacoco:cover
[info] Loading project definition from /Users/johnson/projecthosting/github/play-example-quality-assurance/project
[info] Set current project to play-example-quality-assurance (in build file:/Users/johnson/projecthosting/github/play-example-quality-assurance/)
[info] ApplicationTest
[info] + ApplicationTest.simpleCheck
[info] + ApplicationTest.renderTemplate
[info] 
[info] 
[info] Total for test ApplicationTest
[info] Finished in 0.239 seconds
[info] 2 tests, 0 failures, 0 errors
[info] IntegrationTest
[info] + IntegrationTest.test
[info] 
[info] 
[info] Total for test IntegrationTest
[info] Finished in 2.875 seconds
[info] 1 tests, 0 failures, 0 errors
[info] Passed: : Total 3, Failed 0, Errors 0, Passed 3, Skipped 0
[success] Total time: 4 s, completed Jun 10, 2013 1:51:29 PM
```

The output report is available in target/jacoco/html/index.html.  For Play's default application, statement coverage is 57%.

Jacoco configuration options can be provided in [Build.scala](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/Build.scala).

JavaDoc and ScalaDoc
--------------------

```
[~/projecthosting/github/play-example-quality-assurance]-> play api-doc
[info] Loading project definition from /Users/johnson/projecthosting/github/play-example-quality-assurance/project
[info] Set current project to play-example-quality-assurance (in build file:/Users/johnson/projecthosting/github/play-example-quality-assurance/)
[info] No sources available, skipping Scala API documentation...
[info] Creating destination directory: "target/doc/api/java/"
[info] Loading source files for package controllers...
[info] Loading source files for package tests...
[info] Constructing Javadoc information...
[info] Standard Doclet version 1.7.0_10
[info] Building tree for all the packages and classes...
[info] Generating target/doc/api/java/controllers/Application.html...
[info] Generating target/doc/api/java/tests/ApplicationTest.html...
[info] Generating target/doc/api/java/tests/IntegrationTest.html...
[info] Generating target/doc/api/java/overview-frame.html...
[info] Generating target/doc/api/java/controllers/package-frame.html...
[info] Generating target/doc/api/java/controllers/package-summary.html...
[info] Generating target/doc/api/java/controllers/package-tree.html...
[info] Generating target/doc/api/java/tests/package-frame.html...
[info] Generating target/doc/api/java/tests/package-summary.html...
[info] Generating target/doc/api/java/tests/package-tree.html...
[info] Generating target/doc/api/java/constant-values.html...
[info] Generating target/doc/api/java/src-html/controllers/Application.html...
[info] Generating target/doc/api/java/src-html/tests/IntegrationTest.html...
[info] Generating target/doc/api/java/src-html/tests/ApplicationTest.html...
[info] Building index for all the packages and classes...
[info] Generating target/doc/api/java/overview-tree.html...
[info] Generating target/doc/api/java/index-all.html...
[info] Generating target/doc/api/java/deprecated-list.html...
[info] Building index for all classes...
[info] Generating target/doc/api/java/allclasses-frame.html...
[info] Generating target/doc/api/java/allclasses-noframe.html...
[info] Generating target/doc/api/java/index.html...
[info] Generating target/doc/api/java/overview-summary.html...
[info] Generating target/doc/api/java/help-doc.html...
API documentation in target/doc/api

[success] Total time: 2 s, completed Jun 10, 2013 1:55:36 PM
```

The API documentation can be found in target/doc/api.

NOTE: With this approach, in order for test code to be documented by JavaDoc, you must locate them a package called 
"tests" inside the top-level test/ directory. See this repo for an example.
This is a change from the "play new" command, which puts the sample tests in the default package.  Creating a
"tests" package creates consistency with the existing Play convention of "controllers", "models", and "views"
packages.  

To modify the output, edit [ApiDocSettings.scala](https://github.com/ics-software-engineering/play-example-quality-assurance/blob/master/project/ApiDocSettings.scala).

Credits
=======

  * Checkstyle and PMD integration thanks to Yuvi Masory: https://github.com/ymasory/sbt-code-quality.g8
  * Findbugs integration thanks to Joachim Hofer: https://bitbucket.org/jmhofer/findbugs4sbt/wiki/Home
  * Jacoco integration thanks to Joachim Hofer: https://bitbucket.org/jmhofer/jacoco4sbt
  * JavaDoc/ScalaDoc integration thanks to Yvonnick Esnault: https://github.com/yesnault/Play20StartApp/
  
Play version
------------

Last tested on Play 2.1.1

Build status
------------
  [![Build Status](https://philipmjohnson.ci.cloudbees.com/buildStatus/icon?job=play-example-quality-assurance)](https://philipmjohnson.ci.cloudbees.com/job/play-example-quality-assurance/) 



