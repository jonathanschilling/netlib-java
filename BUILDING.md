# How to build netlib-java using Docker

[Docker images for Debian](https://hub.docker.com/_/debian) are used to build `netlib-java`
for the different versions of `libgfortran.so`.
Here are the version available:
| release name | version number | alias (Apr 2020) | `libgfortran.so`
|--------------|----------------|------------------|-----------------
| jessie       | 8              | oldoldstable     | 3.0.0
| stretch      | 9              | oldstable        |
| buster       | 10             | stable           |
| bullseye     | (11)           | testing          |
| bookworm     | (12)           | unstable         |



