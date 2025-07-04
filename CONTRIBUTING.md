# Contributing to the Akka SDK

FIXME contribution guidelines like in other LB projects


# Project tips

## Build Token

To build locally, you need to fetch a token at https://account.akka.io/token that you have to place into `~/.sbt/1.0/akka-commercial.sbt` file like this:
```
ThisBuild / resolvers += "lightbend-akka".at("your token resolver here")
```

##  Build scripts

1. See `.sh` scripts in the root directory.

2. Set the maven plugin version to the version sbt generated:

`publishLocally.sh` or

    ```shell
    cd akka-javasdk-maven
    mvn versions:set -DnewVersion="0.7...-SNAPSHOT"
    mvn install
    git checkout .
    ```

3. Pass that version to the sample projects when building:

`updateSamplesVersions.sh` or

    ```shell
    cd samples/protobuf-key-value-shopping-cart
    mvn -Dakka-javasdk.version="0.7...-SNAPSHOT" compile
    ```

Be careful not to accidentally check in the `maven` `pom.xml` files with changed version.
