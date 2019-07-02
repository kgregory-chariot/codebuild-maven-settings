# maven-settings

This project contains a default settings.xml for use with AWS Codebuild,
allowing use of a Nexus server. The settings file is adapted from the
[Nexus 3 docs](https://help.sonatype.com/repomanager3/formats/maven-repositories#MavenRepositories-ConfiguringApacheMaven).

Configure via environment variables:

Variable Name       | Description
--------------------|-------------
`NEXUS_GROUP_URL`   | Full URL of the Nexus group repository (for artifact retrieval)

