# maven-settings

This project contains a default settings.xml for use with AWS Codebuild,
allowing use of a Nexus server. The settings file is adapted from the
[Nexus 3 docs](https://help.sonatype.com/repomanager3/formats/maven-repositories#MavenRepositories-ConfiguringApacheMaven).

## Usage

Configure the following environment variables in the build:

Variable Name               | Description
----------------------------|-------------
`NEXUS_GROUP_URL`           | Full URL of the Maven group repository (for artifact retrieval)
`NEXUS_RELEASE_URL`         | Full URL of the Maven release repository (for artifact deployment)
`NEXUS_SNAPSHOT_URL`        | Full URL of the Maven snapshot repository (for artifact deployment)
`NEXUS_DEPLOYMENT_USER`     | Nexus user for deployments.
`NEXUS_DEPLOYMENT_PASSWORD` | Password for deployment user.


Add this project as a secondary source, with the name `Maven_Settings`, and reference it in your Maven command:

```
mvn -B -s ${CODEBUILD_SRC_DIR_Maven_Settings}/settings.xml clean deploy
```


Update your project POM to use the following `distributionManagement`:

```
<distributionManagement>
  <repository>
    <id>nexus</id>
    <name>Releases</name>
    <url>${env.NEXUS_RELEASE_URL}</url>
  </repository>
  <snapshotRepository>
    <id>nexus</id>
    <name>Snapshot</name>
    <url>${env.NEXUS_SNAPSHOT_URL}</url>
  </snapshotRepository>
</distributionManagement>
```
