This deals with generating Extent reports for Cucumber-JVM version 5 for latest ExtentReports version 5.0.0-SNAPSHOT(https://oss.sonatype.org/content/repositories/snapshots/com/aventstack/extentreports/5.0.0-SNAPSHOT/). This is a protoype attempt and is Work in Progress. 

For generating Extent reports for Cucumber-JVM version 5 and ExtentReports version 4.x.x refer to this [article](http://grasshopper.tech/1697/)

To build from source use ```install -Dmaven.test.failure.ignore=true``` or ```install -Dmaven.test.skip=true```. This ignores intentional test failures from stopping the build.



- Download the extentreports-5.0.0 from above location and install in local repository. ```mvn install:install-file -Dfile=<path to downloaded jar> -DgroupId=com.aventstack -DartifactId=extentreports -Dversion=5.0.0-SNAPSHOT -Dpackaging=jar``` OR enable using snapshot versions in pom.xml - https://stackoverflow.com/questions/7715321/how-to-download-snapshot-version-from-maven-snapshot-repository.

- Import the code of this repo and build using - ```install -Dmaven.test.failure.ignore=true``` or ```install -Dmaven.test.skip=true```

- Add below dependency to the project
```
<dependency>
    <groupId>tech.grasshopper</groupId>
    <artifactId>extentreports5-cucumber5-adapter</artifactId>
    <version>1.0.0-SNAPSHOT</version>
</dependency>
```


Points to be noted for running report - 

- This only supports creation of a SparkReport. HTML and Logger reports have been removed in extentreports version 5.

- Make sure the the report output folder structure already exists. If you set ```extent.reporter.spark.out=test-output/Spark``` in extent.properties, then make sure the test-output/Spark folder exists. Else one will get a file named 'Spark' on report generation.

- The ```extent.reporter.spark.config=src/test/resources/extent-config.xml``` will be ignored as the code for reading this xml file is currently commented in ExtentService. This is giving a freemarker configuration error when enabled.

- The duration of test execution seems to be giving wrong values.

- Code in ExtentService is hard coded for SparkReport creation and will be refactored.



