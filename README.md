# KMP Demo

A Kotlin Multiplatform project that supports multiple targets including JVM, macOS, Linux, and Windows.

## Gradle Properties Configuration

The project uses the following configuration in `gradle.properties`:

### Gradle Settings
- `org.gradle.jvmargs=-Xmx4G` - Sets the maximum heap size for Gradle daemon to 4GB
- `org.gradle.caching=true` - Enables Gradle's build cache to improve build performance
- `org.gradle.configuration-cache=true` - Enables Gradle's configuration cache for faster startup
- `org.gradle.daemon=true` - Enables Gradle daemon for faster builds
- `org.gradle.parallel=true` - Enables parallel execution of builds

### Kotlin Settings
- `kotlin.code.style=official` - Uses the official Kotlin coding style
- `kotlin.daemon.jvmargs=-Xmx4G` - Sets the maximum heap size for Kotlin daemon to 4GB
- `kotlin.native.binary.gc=cms` - Sets the garbage collector for Kotlin native binaries to CMS
- `kotlin.incremental.wasm=true` - Enables incremental compilation for WebAssembly targets
- `kotlin.mpp.enableCInteropCommonization=true` - Enables commonization of C interop libraries
- `kotlin.native.ignoreDisabledTargets=true` - Ignores disabled native targets during compilation

### Build Platform Settings
- `build.platform=all` - Sets the build platform to "all" to build for all available platforms (value can be "all" or "platform")
- `build.jvm=true` - Enables JVM build target

## Build Commands

### Building for all platforms
```bash
./gradlew build
```

### Building for specific platforms

To build only for JVM:
```bash
./gradlew build -Pbuild.jvm=true -Pbuild.platform=jvm
```

To build for native platforms only:
```bash
./gradlew build -Pbuild.jvm=false
```

### Release builds
To compile release binaries for all enabled platforms:
```bash
./gradlew release
```

This will create release executables for all enabled platforms (Windows, macOS, Linux) based on the `build.platform` property.

### Platform-specific builds

- For macOS x64: `./gradlew linkReleaseExecutableMacosX64`
- For macOS ARM64: `./gradlew linkReleaseExecutableMacosArm64`
- For Linux x64: `./gradlew linkReleaseExecutableLinuxX64`
- For Windows x64: `./gradlew linkReleaseExecutableMingwX64`

## Project Structure

The project is organized as a Kotlin Multiplatform Project with:
- Common source code in `app/src/commonMain/kotlin`
- Platform-specific implementations for JVM, macOS, Linux, and Windows
- Gradle build scripts in `buildSrc` for reusable build logic