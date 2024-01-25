# AppHack

A script for automating the reverse engineering and rebuilding process of an APK.

## Functions

First, a specified input APK is extracted with apktool. Then the supplied "hacked" files are configured and added to the APK. Finally, the APK is rebuild with the applied changes.

## Dependencies

- [Apktool](https://apktool.org/)
- Android SDK or only `sudo apt install aapt apksigner zipalign`
- and a Java installation including [keytool](/usr/lib/jvm/java-11-openjdk-amd64/bin/keytool)

## Usage

```
./apkhack <input apk> [-s]
```

- `-s`: Serve the build directory via HTTP.

The "hacked" files are supplied in a directory named `src` inside the project root directory. The files are replacing files with exact the same name in the extracted APK directory. This is for convenience, but may elict the problem of duplicates or adding files without replacing them. Since I don't need it for now, I'll leave it for now.

A config file can be supllied named `config` in the project root directory. This file has to have key-value-pairs, one per line, seperated by a semicolon. Example:

```
###FIRSTNAME###;Mister
###LASTNAME###;Smith
```

This config file is taken to replace occurences of the keys with the values inside files in the `src` directory.
