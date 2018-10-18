# Android Signing

This article serves as notes of my Android signing study.

# Android Signing Schemes
Android signing has three types which will be described in subsequent sections.
* v1
* v2
* v3

## Android Signing v1
Android signing v1 is essentially an apk signed using jarsigner that comes with the Java JDK.

## Android Signing v2
Android signing v2 was introduced in Android 7.0 and uses a new application to sign.
v2 uses apksigner instead of jarsigner. apksigner was added in Build Tools revision 24.0.3

An apk signed with apksigner is compatible with v1. By default, apksigner signs APKs using the conventional JAR signing scheme (used by jarsigner) and the APK Signature Scheme v2 introduced in Android 7.0 (API level 24). 
An apk must be zipaligned before v2 signing and after signing, v2 will preserve alignment and compression. Hence there is no need to zipalign after signing.

If an apk is already signed, the existing signature is replaced with the new signature. No manual removal of META-INF is necessary.

## Android Signing v3
Android signing v3 was introduced in Android 9.0 and is v2 signing which includes additional information in the signing block but otherwise works the same. 

An excerpt from Google documentation explains how v3 works:

_Android 9 supports APK key rotation, which gives apps the ability to change their signing key as part of an APK update. To make rotation practical, APKs must indicate levels of trust between the new and old signing key. To support key rotation, we updated the APK signature scheme from v2 to v3 to allow the new and old keys to be used. V3 adds information about the supported SDK versions and a proof-of-rotation struct to the APK signing block._

# Reference

* [Android Application Signing](https://source.android.com/security/apksigning/index.html#v1)
* [Build Tools release notes](https://developer.android.com/studio/releases/build-tools)
* [apksigner](https://developer.android.com/studio/command-line/apksigner)
* [v3 scheme](https://source.android.com/security/apksigning/v3)