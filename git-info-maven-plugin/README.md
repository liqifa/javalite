# GitInfo is a Maven plugin which generates HTML file with stats for the current project

This plugin generates a file that contains some information about the project.
This file later can be used to peg the binary application file to a specific
revision in Git so as to help production support. This file will answer questions:

* When was it built?
* Where was it built?
* What revision was it built from?
* What branch it belongs to?

## Generated file

The file that is generated by plugin is called `git_info.html`, and is located at the root of classpath (`target/classes`).

## Configuration

To configure this plugin, add this block to your pom:


    <plugin>
        <groupId>com.javalite</groupId>
        <artifactId>git-info-maven-plugin</artifactId>
        <version>1.4.12</version>
        <executions>
            <execution>
                <phase>compile</phase>
                <goals>
                    <goal>generate</goal>
                </goals>
            </execution>
        </executions>
    </plugin>


## Exposing information


The file `git_info.html` is going to be available on the root of classpath, and applications can expose it in different ways.
If this is a web application, it makes sense to create a URL that will simply expose this file.
For non-web apps, this file might not have to be exposed, but still nice to have it packaged into the app
to assist figuring problems in production.

# Non-Maven usage

Functionality is encapsulated in a class `org.javalite.maven.GitInfo`. Any non-Maven project can source this plugin
as standard dependency on classpath and then use this call:

`
String html = com.javalite.maven.GitInfo.getHtml();
`