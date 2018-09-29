A sample project to reproduce a Kotlin compiler warning since AGP 3.3.0-alpha04

## Issue

when setting `allWarningsAsErrors = true` in the kotlin compiler options, build fails with the following error/warning:

```
./gradlew assemble
w: Some JAR files in the classpath have the Kotlin Runtime library bundled into them. This may cause difficult to debug problems if there's a different version of the Kotlin Runtime library in the classpath. Consider removing these libraries from the classpath
e: warnings found and -Werror specified
w: /Users/User/.gradle/caches/modules-2/files-2.1/com.android.tools.build/builder/3.3.0-alpha12/7fe1b21b121e92cd4e6d6f66116326c5aa826645/builder-3.3.0-alpha12.jar: Library has Kotlin runtime bundled into it

```

## Versions

AGP: `from 3.3.0-alpha04 to 3.3.0-alpha12`

Kotlin: `1.2.71`

## Other info

Prior to release `3.3.0-alpha04` a similar warning (about stdlib-jre being deprecated) could be fixed by excluding the runtime from the plugin:

`exclude module: 'kotlin-stdlib-jre8'`

Starting from version `3.3.0-alpha04` excluding the jre8 or the jdk8 which `3.3.0-alpha12` started using doesn't seem to do anything.
