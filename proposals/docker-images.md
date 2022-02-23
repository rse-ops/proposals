_Container Bases_

This project focused on developing [docker-images](https://github.com/rse-ops/docker-images),
a set of container bases that can be used by other rse-ops and lab projects.

1. A base container is a base operating system typically with spack and compilers installed
2. A matrix image is one level above that, with typically a core piece of software across several versions
3. Both base images and matrix builds are triggered on a nightly basis using updated dependencies.

## Use Cases

I have an open source project that requires cmake and a particular stack of software that
is easily built with the spack package manager. I can easily start with a base image to
save hours of build time, and optimally build and test my own project without worrying about
building the base environment.

## Deliverables

The deliverables for this proposal included:

 1. A set of core builds derived from Dockerfile and other metadata files in [rse-ops/docker-files](https://github.com/rse-ops/docker-images)
 2. Automated workflows to run nightly to rebuild bases and matrix containers
 3. A self-updating web interface to find the latest containers and versions at [rse-ops.github.io/docker-images](https://rse-ops.github.io/docker-images)
 4. A custom pull request / merge workflow that only triggers builds for changes.

Opportunities for extension include adding other bases, architectures, or matrix builds.

## Collaborations

* RADIUSS
* code teams

## Needs

The only need is a GitHub repository with support for running workflows.
