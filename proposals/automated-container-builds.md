_For LLNL Open Source projects_

This is a [Special Projects](https://docs.google.com/document/d/1XCiU_pPe-LwDUUjzEafKc5aWIX04svZH2pH8M-HEIYI/edit#) proposal #1

A main goal of Special Projects is to enable LLNL software to run easily in various computing environments. In this proposal we will introduce automated container builds for the LLNL open source ecosystem which we believe has the potential to improve LLNL software portability while adding minimal overhead to existing code-team workflows. This project includes:
1. Creating automated GitHub & GitLab workflow templates for building & publishing containerized applications. (e.g. Workflows could be run on merge into main or develop, nightly, on release.)
2. Deploying workflows into active LLNL open source project repositories.
3. Working with code teams on both 2 and 3.

While some LLNL projects are embracing the set of [rse-ops docker images](https://rse-ops.github.io/docker-images), likely many are more hesitant. Along with providing us a set of scientific software containers to use for further development and examples for our projects, this first project will engage with code teams directly to show them how they can easily trigger an automated build.

### Use Cases

I am an LLNL developer, interested collaborator, or outside contributor that wants to build on top of LLNL software. Right now to get started with an LLNL project I need to download the source code, install complex dependencies, and build the project to get started. With pre-built containers, the development stack is ready to go, and I simply need to pull it to get started. Containers can also help with portability since I can now develop my software for a known LLNL base container without worrying about my local HPC environment.


### Lab Influence

Providing containers with automated builds for the lab is the first step to not just improving the developer experience or extending our software to different environments, but also making it easier for external collaborators to develop and try LLNL software. It’s also an opportunity for the Special Projects team to engage with code teams, demonstrating to them an easy way to link their repositories and our builds with an automated trigger. 


### Deliverables

The deliverables for this proposal include:

* Automated builds and updates of LLNL software.

Opportunities for extension include providing similar functionality for other CI services (e.g., Azure pipelines or GitLab).


### Collaborations

* Various Code Teams

We will engage with the code teams to show them a workflow step they can add to perform the build alongside their project.
