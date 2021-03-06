---
layout: post
title:  "Migrating from Java 8 to Java 11"
date:   2020-01-13 21:47:57 +0100 
permalink: /java-11-migration/
---

# Why do you need to migrate now?

- JDK 8 support was ending in 2020, unless you purchase commercial license ([1])
- Improved Security :&nbsp;TLS 1.3 implementation, better SSL-validation, deprecated old ciphers,.. ([2])
- Faster, improved garbage collection
- Default container-support, like with Docker ([3])
- Extra language features : like 'var' keyword, Optional-Stream, extra Stream-methods, handy collection-functions like Lists.of(…),…
- Safer reflection-operations

# How to start

- Select your JDK version:
  - Every 6 months there will be a new major version of Java. It's best to choose a version with long time support like Java 11, 14, 17,...
  - There are several commercial providers, but also free and good alternatives like [OpenJDK](https://adoptopenjdk.net/) ([4])
- Update your tools:
  - Maven 3.5+, Compiler 3.8+, surefire &amp; failsafe plugins 2.22+
- Change the version of Java in your project, so add in your pom-file
  {% highlight xml %}
  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
    <java.version>11</java.version>
    <maven.compiler.source>${java.version}</maven.compiler.source>
    <maven.compiler.target>${java.version}</maven.compiler.target>
  </properties>
  {% endhighlight %}
- In your IDE change the version of your modules to JDK 11 and change the language level to Java 11. (In IntelliJ : short-cut F4)
- The ultimate test is to use somewhere in your code the 'var'-keyword: Recompile, run all the tests and start the application. If everythings works : the migration is a succes
- As final step it is often needed to update your pipeline or CI/CD: 
  - The security-configuration file got moved to the config-folder of your JVM
  - The command-line arguments are now easier, like `-XX:+UseContainerSupport` is now default ([5])

# Known problems
- Java EE modules got removed ([6])
  - Exceptions like `Exception in thread "main" java.lang.NoClassDefFoundError: javax/xml/bind/JAXBException`. Just include:
    {% highlight xml %}
    <dependency>
      <groupId>com.sun.xml.bind</groupId>
      <artifactId>jaxb-impl</artifactId>
      <version>2.3.2</version>
    </dependency>
    {% endhighlight %}  
- Embedded Postgres database gave some issues and this fixes it. Alternatively you can use [Test Containers](https://www.testcontainers.org/).
  {% highlight xml %}
  <dependency>
    <groupId>ru.yandex.qatools.embed</groupId>
    <artifactId>postgresql-embedded</artifactId>
    <scope>test</scope>
    <!-- temp fix for JDK 11 annoying postgress shutdown exceptions, awaiting release new version -->
    <!-- https://github.com/yandex-qatools/postgresql-embedded/issues/153  -->
    <exclusions>
      <exclusion>
        <groupId>de.flapdoodle.embed</groupId>
        <artifactId>de.flapdoodle.embed.process</artifactId>
      </exclusion>
    </exclusions>
  </dependency>
  <dependency>
    <groupId>de.flapdoodle.embed</groupId>
    <artifactId>de.flapdoodle.embed.process</artifactId>
    <version>2.0.5</version>
  </dependency>
  {% endhighlight %}
- SSL-issues: they were due to more validation by Java 11. This is normally all fixed now.
- Exceptions where they complain about the byte code version mismatch. Just remember that byte code of Java 8 is version 52 and the byte code of Java 11 is version 55. 
  You probably didn't rebuild all modules or somewhere there is a wrong Java version declared. 
  The exception is normally very verbose and easy to understand ([7])
  
[1]: https://www.oracle.com/technetwork/java/java-se-support-roadmap.html
[2]: https://hub.packtpub.com/java-11-is-here-with-tls-1-3-unicode-11-and-more-updates/ 
[3]: https://blog.softwaremill.com/docker-support-in-new-java-8-finally-fd595df0ca54
[4]: https://docs.google.com/document/d/1nFGazvrCvHMZJgFstlbzoHjpAVwv5DEdnaBr_5pKuHo/edit#heading=h.p3qt2oh5eczi
[5]: https://stackoverflow.com/questions/54516988/what-does-usecontainersupport-vm-parameter-do
[6]: https://blog.codefx.org/java/java-11-migration-guide/
[7]: https://en.wikipedia.org/wiki/Java_class_file
