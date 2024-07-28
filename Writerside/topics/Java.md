# Java

## Steps to Run Astronuts Code Quality Checks on your Java Project {id="java-code-quality-steps"}
Note* : Astronuts code quality action only supports Jacoco and Cobertura code coverage library for build systems Gradle and Maven.
<tabs>
    <tab id="gradle" title="Gradle">
<tabs>
<tab title="Jacoco">
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
<tab title="Cobertura">
<code-block lang="groovy">
// Apply the Cobertura Plugin to capture and visualize code coverage testing results.
plugins {
    id 'net.saliman.cobertura' version '4.0.0'
}
// Add Repositories
// Ensure your project uses mavenCentral for resolving dependencies:
repositories {
mavenCentral()
}
// Add the necessary dependencies for your project and testing:
dependencies {
implementation 'com.google.guava:guava:31.0.1-jre'
testImplementation 'org.junit.jupiter:junit-jupiter:5.8.1'
testRuntimeOnly 'org.junit.platform:junit-platform-launcher:1.8.1'
}
// Configure Java Toolchain
// Specify the Java toolchain for the project:
java {
toolchain {
languageVersion = JavaLanguageVersion.of(21)
}
}
// Configure Test Task
// Ensure the test task is configured to generate Cobertura reports after tests run:
test {
finalizedBy 'coberturaReport' // report is always generated after tests run
}
tasks.named('test') {
// Use JUnit Platform for unit tests.
useJUnitPlatform()
}
// Configure Cobertura
// Add configuration for generating Cobertura reports:
cobertura {
coverageFormats = ['xml']
coverageSourceDirs = sourceSets.main.allSource.srcDirs
includeSourceDirs = true
coverageReportDir = file("$buildDir/reports/cobertura")
}
// Ensure the build task depends on the Cobertura report task
tasks.build {
dependsOn 'coberturaReport'
}
</code-block>
</tab>
</tabs>
    </tab>
    <tab id="maven" title="Maven">
<tabs>
<tab title="Jacoco">
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
<tab title="Cobertura">
<code-block lang="xml">
 <![CDATA[
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>example-project</artifactId>
    <version>1.0-SNAPSHOT</version>
    <properties>
        <maven.compiler.source>21</maven.compiler.source>
        <maven.compiler.target>21</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <cobertura.version>2.7</cobertura.version>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.google.guava</groupId>
            <artifactId>guava</artifactId>
            <version>31.0.1-jre</version>
        </dependency>
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
    </dependencies>
    <build>
        <plugins>
            <!-- Configure the Maven Compiler Plugin -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>${maven.compiler.source}</source>
                    <target>${maven.compiler.target}</target>
                </configuration>
            </plugin>
            <!-- Configure the Maven Surefire Plugin to use JUnit 5 -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>2.22.2</version>
                <configuration>
                    <includes>
                        <include>**/*Tests.java</include>
                    </includes>
                    <properties>
                        <property>
                            <name>junit.jupiter.extensions.autodetection.enabled</name>
                            <value>true</value>
                        </property>
                    </properties>
                </configuration>
            </plugin>
            <!-- Apply the Cobertura Plugin to generate code coverage reports -->
            <plugin>
                <groupId>org.codehaus.mojo</groupId>
                <artifactId>cobertura-maven-plugin</artifactId>
                <version>${cobertura.version}</version>
                <configuration>
                    <formats>
                        <format>xml</format>
                    </formats>
                </configuration>
                <executions>
                    <execution>
                        <id>cobertura</id>
                        <goals>
                            <goal>cobertura</goal>
                        </goals>
                        <phase>test</phase>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
</project>
]]>
</code-block>
</tab>
</tabs>
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