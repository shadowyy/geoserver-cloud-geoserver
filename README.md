# GeoServer Cloud GeoServer

This is the deployment repository for the customized GeoServer version used by GeoSever Cloud

## Install and deploy

On a local machine, before pushing to this github repository, in order to test the artifacts, run


```
make install
```

The CI build runs instead

```
make deploy
```

> `install` does not need to be run before `deploy`

## 构建
### 不要带单引号
```cmd
mvn clean install -f geoserver/src/pom.xml -DskipTests
```

## 发布
### snapshot版
```cmd
mvn deploy -f geoserver/src/pom.xml --batch-mode -DskipTests -ntp -Dsort.skip=true -Dspotless.apply.skip=true -DaltSnapshotDeploymentRepository=huitongnav-maven-snapshots::http://nexus.huitongnav.corp/repository/maven-snapshots/ -Prelease,pending,communityRelease
```
### release版本
```cmd
mvn deploy -f geoserver/src/pom.xml --batch-mode -DskipTests -ntp -Dsort.skip=true -Dspotless.apply.skip=true -DaltDeploymentRepository=huitongnav-maven-releases::http://nexus.huitongnav.corp/repository/maven-releases/ -Prelease,pending,communityRelease
```

## 构建和发布release版本
```cmd
mvn clean deploy -f geoserver/src/pom.xml --batch-mode -DskipTests -ntp -Dsort.skip=true -Dspotless.apply.skip=true -DaltDeploymentRepository=huitongnav-maven-releases::http://nexus.huitongnav.corp/repository/maven-releases/ -Prelease,pending,communityRelease
```