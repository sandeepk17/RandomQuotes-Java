A sample Java application to display famous quotes.

Run `mvn package` to create JAR, and `mvn package -Pwar` to create WAR.

To deploy to Sonatype (https://oss.sonatype.org/#welcome) run the command:

```
mvn -Psonatype "-Dgpg.keyname=gpgkeyname" "-Dgpg.passphrase=keypassword" clean deploy
```

Note that you need to configure `~/.m2/settings.xml` with your Sonatype credentials. 
See https://central.sonatype.org/pages/apache-maven.html for details.

The WAR file has been published as `com.octopus:randomquotes`, and is available on
[Maven central](https://repo1.maven.org/maven2/com/octopus/randomquotes/).