# Ad Service

The Ad service provides advertisement based on context keys. If no context keys
are provided then it returns random ads.

## Building Locally

- Install Java

```ssh
sudo apt install jdk-21-jre-headless
```

The Ad service requires at least JDK 17 to build and uses gradlew to
compile/install/distribute. Gradle wrapper is already part of the source code.
To build Ad Service, run:

```sh
./gradlew installDist

<or>

./gradlew installDist -PprotoSourceDir=./proto
```

- So this command here is going to start the Gradle daemon which is like a server. And it is going to install the dependencies, Then it is going to perform the compilation.
Also it is going to build the application and the build application is saved in a particular directory, which is also provided by the directory developer.

<img width="1045" height="340" alt="image" src="https://github.com/user-attachments/assets/ed8e8aaf-7dd3-40a4-b6db-e83eeb82ce06" />


It will create an executable script
`src/ad/build/install/oteldemo/bin/Ad`.

To run the Ad Service:

```sh
export AD_PORT=8080
export FEATURE_FLAG_GRPC_SERVICE_ADDR=featureflagservice:50053
./build/install/opentelemetry-demo-ad/bin/Ad
```

### Upgrading Gradle

If you need to upgrade the version of gradle then run

```sh
./gradlew wrapper --gradle-version <new-version>
```

## Building Docker

From the root of `opentelemetry-demo`, run:

```sh
docker build --file ./src/ad/Dockerfile ./
```
