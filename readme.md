## build instructions

* install gomobile

```bash
go install golang.org/x/mobile/cmd/gomobile@latest
```

* build yggdrasil-go for android:

```
git clone https://github.com/yggdrasil-network/yggdrasil-go /tmp/yggdrasil-go
cd /tmp/yggdrasil-go
./contrib/mobile/build -a
```

* build blemesh-android:

```
git clone https://codeberg.org/aakselrod/blemesh-android /tmp/blemesh-android
cd /tmp/blemesh-android
./gradlew build assemble
```

* clone yggdrasil for android and copy over the built go library

```
git clone https://github.com/yggdrasil-network/yggdrasil-android /tmp/yggdrasil-android
mkdir /tmp/yggdrasil-android/app/libs
cp /tmp/yggdrasil-go/yggdrasil.aar /tmp/yggdrasil-android/app/libs/
cp /tmp/blemesh-android/lib/build/outputs/aar/lib-release.aar /tmp/yggdrasil-android/app/libs/blemesh.aar
```

* build yggdrasil-android

```
cd /tmp/yggdrasil-android
./gradlew assembleRelease
```

note: you will need to use jdk-11 as jdk-16 `"doesn't work" ™`

on debian/ubuntu you can set which jdk used with the `JAVA_HOME` env var:
```
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64/
```
