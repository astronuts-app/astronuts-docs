# Java

## Steps to Run Astronuts Code Quality Checks on your Python Project

<tabs>
    <tab id="gradle" title="gradle">
        <code-block lang="groovy">
// Apply the JaCoCo Plugin to capture and visualize code coverage testing results.
apply plugin: 'jacoco'
//Add Repositories
//Ensure your project uses mavenCentral for resolving dependencies:
repositories {
    mavenCentral()
}
//Add the necessary dependencies for your project and testing:
dependencies {
    implementation 'com.google.guava:guava:31.0.1-jre'
    testImplementation 'org.junit.jupiter:junit-jupiter:5.8.1'
    testRuntimeOnly 'org.junit.platform:junit-platform-launcher:1.8.1'
}
//Configure Java Toolchain
//Specify the Java toolchain for the project:
java {
    toolchain {
        languageVersion = JavaLanguageVersion.of(21)
    }
}
// Configure Test Task
// Ensure the test task is configured to generate JaCoCo reports after tests run:
test {
    finalizedBy jacocoTestReport // report is always generated after tests run
}
tasks.named('test') {
    // Use JUnit Platform for unit tests.
    useJUnitPlatform()
}
// Configure JaCoCo
// Add configuration for generating JaCoCo reports:
jacocoTestReport {
    dependsOn test // tests are required to run before generating the report
    reports {
        xml.required = true
    }
}
tasks.build {
    dependsOn jacocoTestReport
}
</code-block>
    </tab>
    <tab id="maven" title="maven">
        <code-block lang="xml">
<![CDATA[
<!-- Step-by-Step Guide to Configure JaCoCo in a Maven Project -->
<!-- 1. Add the JaCoCo Plugin -->
<!--To capture and visualize code coverage testing results, you need to include the JaCoCo plugin in your Maven `pom.xml`. -->
<plugin>
    <groupId>org.jacoco</groupId>
    <artifactId>jacoco-maven-plugin</artifactId>
    <version>0.8.7</version>
    <executions>
<!-- Prepare the JaCoCo agent before tests run -->
        <execution>
            <goals>
                <goal>prepare-agent</goal>
            </goals>
        </execution>
<!-- Generate JaCoCo report after tests run -->
        <execution>
            <id>report</id>
            <phase>test</phase>
            <goals>
                <goal>report</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <outputDirectory>${project.build.directory}/jacoco</outputDirectory>
    </configuration>
</plugin>
<!-- 2. Add Repositories -->
<!-- Ensure your project uses Maven Central for resolving dependencies by adding the following repository configuration: -->
<repositories>
    <repository>
        <id>central</id>
        <url>https://repo.maven.apache.org/maven2</url>
    </repository>
</repositories>
<!--3. Add Necessary Dependencies -->
<!-- Include the necessary dependencies for your project and testing: -->
<dependencies>
<!-- Project dependency -->
    <dependency>
        <groupId>com.google.guava</groupId>
        <artifactId>guava</artifactId>
        <version>31.0.1-jre</version>
    </dependency>
<!-- JUnit 5 dependencies for testing -->
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-api</artifactId>
        <version>5.8.1</version>
        <scope>test</scope>
    </dependency>
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-engine</artifactId>
        <version>5.8.1</version>
        <scope>test</scope>
    </dependency>
    <dependency>
        <groupId>org.junit.platform</groupId>
        <artifactId>junit-platform-launcher</artifactId>
        <version>1.8.1</version>
        <scope>test</scope>
    </dependency>
</dependencies>
<!-- 4. Configure the Java Toolchain -->

<!-- Specify the Java toolchain for your project by setting the Java version in the `properties` section: -->
<properties>
    <maven.compiler.source>21</maven.compiler.source>
    <maven.compiler.target>21</maven.compiler.target>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
</properties>
<!--5. Configure the Test Task -->

<!--Ensure the `test` task is configured to generate JaCoCo reports after tests run by setting up the Surefire plugin:-->
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>2.22.2</version>
    <configuration>
        <useSystemClassLoader>false</useSystemClassLoader>
    </configuration>
    <dependencies>
        <dependency>
            <groupId>org.junit.platform</groupId>
            <artifactId>junit-platform-surefire-provider</artifactId>
            <version>1.8.1</version>
        </dependency>
    </dependencies>
</plugin>
]]>
        </code-block>
    </tab>
</tabs>
## Integration with CI/CD Workflow
You can integrate Astronuts Code Quality action into your build scripts, which is especially useful in continuous integration (CI) environments where tests are run automatically.
Add this to your workflow file to run Astronuts Code Quality Checks on your Java project:
<tabs>
    <tab id="workflow-java" title="gradle">
        <code-block lang="yaml">
      - name: Run Astronuts Code Quality Checks
        uses: astronuts-app/astronuts-code-quality-action@v4
        with:
          sourceLanguage: 'java'
          buildSystem: 'gradle'
      </code-block>
    </tab>
    <tab id="workflow-maven" title="maven">
        <code-block lang="yaml">
      - name: Run Astronuts Code Quality Checks
        uses: astronuts-app/astronuts-code-quality-action@v4
        with:
          sourceLanguage: 'java'
          buildSystem: 'maven'
      </code-block>
    </tab>
</tabs>

For more info you can check
the [Astronuts Code Quality Action](https://github.com/marketplace/actions/astronuts-code-quality-action).

For more info on the workflow file, you can check
the [GitHub Actions Workflow Sample](https://github.com/astronuts-app/samples/blob/main/.github/workflows/build_java_sample.yml).