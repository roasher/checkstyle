# Checkstyle

## Why

To take benefit from solid single project code style.

## What

Maven project with:

* checkstyle.xml that has rules inside. Build based on Google checkstyle but not so strict.
* IntelliJ code style file

## Usage

* Add this to your pom.xml

```
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-checkstyle-plugin</artifactId>
    <version>3.2.1</version>
    <dependencies>
        <dependency>
            <groupId>com.puppycrawl.tools</groupId>
            <artifactId>checkstyle</artifactId>
            <version>10.9.0</version>
        </dependency>
        <dependency>
          <groupId>ru.yurkinsworkshop</groupId>
          <artifactId>checkstyle</artifactId>
          <version>1.1</version>
        </dependency>
    </dependencies>
    <configuration>
        <sourceDirectories>${basedir}/src</sourceDirectories>
        <configLocation>checkstyle.xml</configLocation>
        <encoding>UTF-8</encoding>
        <includeTestSourceDirectory>true</includeTestSourceDirectory>
    </configuration>
    <executions>
        <execution>
            <id>validate</id>
            <phase>validate</phase>
            <goals>
                <goal>check</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

Now, checkstyle will be included in your validation step, which is almost every step in maven.

Try
```mvn compile```, you should see checkstyle triggered along compilation:
```
[INFO] --- maven-checkstyle-plugin:3.2.1:check (validate) @ ${project name} ---
```

* Import IntelliJIdea_checkstyle.xml as a scheme inside IntelliJ: Settings -> Editor -> Code Style -> Java -> Scheme -> Import Scheme
  -> IntelliJ IDEA Code style XML. Now you can select src project folder and trigger reformat code.
