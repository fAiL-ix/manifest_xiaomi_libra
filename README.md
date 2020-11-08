# Xiaomi Mi 4C local_maifest file to build Lineage-17.1

## Setting up the sources
start with adding the LineageOS trees:
`repo init -u git://github.com/LineageOS/android.git -b lineage-17.1`

Place the `libra.xml` file in the `.repo/local_manifests/` directory and sync

`repo sync`

## Applying patches

To build this ROM you have to apply some patches. All available patches can be found in the `device/xiaomi/libra/patch/` directory.

The mandatory patches to be able to build the rom are:

- `build/make/*`
- `frameworks/base/` the `remove-dropbox-service.patch` and `remove-unneeded-overlay.patch` patches
- `packages/apps/Bluetooth/*`
- `system/apex/*`
- `system/core/` `disable-libcutils-trace.patch`, `remove-unneeded-directory.patch` and for user builds: `allow-permissive.patch`
- `system/sepolicy/*` for user builds

To apply a patch, navigate to the folder in the sources. For example for the make patches navigate to `build/make`.
In the directory issue the command
`git am <path/to/the/file.patch`

In our example it would be:
`git am ../../device/xiaomi/libra/patch/build/make/*`


## Using a Docker image to build

You can use [my dockerfile](https://github.com/fAiL-ix/docker-lineageos) to create a docker image which has all the neccessary dependecies which are needed to build this ROM.
