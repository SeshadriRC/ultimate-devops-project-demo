# Ad Service

The Ad service provides advertisement based on context keys. If no context keys
are provided then it returns random ads.

## Building Locally

- Install Java

```ssh
sudo apt install openjdk-21-jre-headless
java --version
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

<img width="1919" height="705" alt="image" src="https://github.com/user-attachments/assets/7ae28ff0-132a-4694-8b61-d0f79185b9fa" />


It will create an executable script

```
./build/install/opentelemetry-demo-ad/bin/
```

<img width="1481" height="427" alt="image" src="https://github.com/user-attachments/assets/638b5f21-3c52-473a-a51a-eca8f9885560" />


To run the Ad Service:

```sh
export AD_PORT=9099
export FEATURE_FLAG_GRPC_SERVICE_ADDR=featureflagservice:50053
./build/install/opentelemetry-demo-ad/bin/Ad
```
- Service is running
<img width="1645" height="222" alt="image" src="https://github.com/user-attachments/assets/967e3252-aa28-48d4-a21d-a1cdfddc708e" />


### Upgrading Gradle           

- I haven't run this, as i didn't faced any error.

If you need to upgrade the version of gradle then run

```sh
./gradlew wrapper --gradle-version <new-version>
```

## Building Docker

From the root of `opentelemetry-demo`, run:

```sh
docker build -t sesharc/adservice:v1
docker run sesharc/adservice:v1
```

<img width="1919" height="610" alt="image" src="https://github.com/user-attachments/assets/fe5ebb7e-35bf-48f9-9571-31ea47545719" />

