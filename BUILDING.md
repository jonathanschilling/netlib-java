# How to build netlib-java using Docker

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



