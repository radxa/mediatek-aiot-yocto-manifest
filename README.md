# Mediatek AIot Yocto

## Build Images for Mediatek Genio boards

Download recipe with manifests.

```
$ mkdir iot-yocto; cd iot-yocto
$ export PROJ_ROOT=`pwd`
$ repo init -u https://github.com/radxa/mediatek-aiot-yocto-manifest.git -b main -m rity-kirkstone-v24.0.xml --no-repo-verify
$ repo sync
```

Build configuration.

```
$ TEMPLATECONF=$PWD/src/meta-rity/meta/conf source src/poky/oe-init-build-env
$ export BUILD_DIR=`pwd`
```

Enable components that require NDA access (optional).

```
$ echo NDA_BUILD = \"1\" >> ${BUILD_DIR}/conf/local.conf
```

Setup paths for downloads and sstate-cache folders.

```
$ echo DL_DIR = \"\${TOPDIR}/../downloads\" >> ${BUILD_DIR}/conf/local.conf
$ echo SSTATE_DIR = \"\${TOPDIR}/../sstate-cache\" >> ${BUILD_DIR}/conf/local.conf
```

### Build Radxa NIO 12L with DDR-4GB

```
$ MACHINE=genio-1200-radxa-nio-12l-d4 bitbake rity-demo-image
```

The output image is located in $BUILD_DIR/tmp/deploy/images/genio-1200-radxa-nio-12l-d4.

### Build Radxa NIO 12L with DDR-8GB

```
$ MACHINE=genio-1200-radxa-nio-12l-d8 bitbake rity-demo-image
```

The output image is located in $BUILD_DIR/tmp/deploy/images/genio-1200-radxa-nio-12l-d8.

### Build Radxa NIO 12L with DDR-16GB

```
$ MACHINE=genio-1200-radxa-nio-12l-d16 bitbake rity-demo-image
```

The output image is located in $BUILD_DIR/tmp/deploy/images/genio-1200-radxa-nio-12l-d16.
