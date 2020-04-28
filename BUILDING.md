# How to build netlib-java using Docker

`netlib-java` consists of various bits and pieces:
- The `native-system` netlib libraries and their dependencies should be available on the target system.
- The `native-ref` netlib libraries are shipped in the `jar`s along with the Java classes
  and have to be compiled for all supported target architectures and commonly found versions of `libgfortran`.
- The `f2j-ref` netlib implementation is a pure Java version obtained from the original Fortran sources by
  use of `f2j`.

All Java parts are compiled using `openjdk-8-jdk` and assembled using Apache `maven`.

The native parts of the code are built depending on the target architecture:
- all macOS-related stuff is built and tested on the macOS CI runners provided by GitHub
- all other binaries are build, i.e. (cross-)compiled on Linux for the various architectures
- testing of the binaries compatible with `amd64` is done directly on the CI runners
- testing of all other binaries is done using Docker's multiarch support via `binfmt_misc`;
  see e.g. https://www.docker.com/blog/multi-platform-docker-builds/ for details.

## Supported targets

[Docker images for Debian](https://hub.docker.com/_/debian) are used to build `netlib-java`
for the different versions of `/usr/lib/x86_x64-linux-gnu/libgfortran.so`.
Here are the version available:
| release name | version number | alias (Apr 2020) | `gfortran` | `libgfortran.so` |
|--------------|----------------|------------------|------------|------------------|
| jessie       | 8              | oldoldstable     | 4.9.2      | 3.0.0            |
| stretch      | 9              | oldstable        | 6.3.0      | 3.0.0            |
| buster       | 10             | stable           | 8.3.0      | 5.0.0            |
| bullseye     | (11)           | testing          | 9.3.0      | 5.0.0            |
| bookworm     | (12)           | unstable         | x.x.x      | x.x.x            |

For Debian Jessie, some tricks are required to get `jessie-backports` for Java 8:
https://unix.stackexchange.com/questions/508724/failed-to-fetch-jessie-backports-repository

## Supported architectures

