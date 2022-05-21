---
title: Research Software Registry
layout: proposal
tags: 
 - draft
---

## Research Software Registry

_catalog and deployment for research software_

We would like an institution to be able to easily deploy a "research software registry" - or a means
to create a catalog of the research software developed at their institution that can easily be deployed
to a development environment. Our vision includes the following:

 - automated builds from a GitHub repository that trigger on custom events
 - an ability to package software, metadata, and SBOMs alongside one another. This is what we call a "research software package"
 - an ability to create citation and credit trees for software.

This is really the "pie in the sky" because the registry isn't just for metadata, but is a way to make using the software totally seamless. 
Select your software, get it installed into a container, and go! But actually, if we design the registry intelligently, we can empower the deploying user to add whatever additional functionality they might want. E.g., a social media posting bot is a plugin you can install, a plugin that generates citations or graphs, or a builder/packager. It's up to the institution that deploys the registry. And I think if we did this right, we'd have social elements around it too - e.g., an annual "State of the Research Software Ecosystem" report and/or meetups to get people with similar software talking. And maybe if an institution is too small and can't deploy their own registry there could be a central one with a 'free tier."


### Research Software Engineers

We can imagine that there is some "research software" engineer group at an institution, or a related group in charge of software curation and community engagement. This group would deploy a registry. With the registry:

1. an institutional researcher or research software engineer can submit their software
2. software in the registry can easily be deployed to development environments, assessed for dependency credit and usage, or cited.
3. an external collaborator can, via the registry interface, assemble a developer environment with custom software.

If an institution doesn't have it's own registry there could be a public one, akin to Docker Hub. Otherwise, this group takes charge of managing the registry. By default, a user can login (and authenticate) via their Github account to generate a token, and add a custom workflow to do a build and deploy of their software to GitHub packages. This event, on success, will notify the registry, and submit the software entry to be available, and also update metadata about dependencies that can be used to summarize the ecosystem of the registry. This is along the lines of the vision of [CiteLang](https://github.com/vsoch/citelang). Additionally, these registries might be customizable. There are [many reasons](https://gist.github.com/vsoch/d77254b2a7032b6ad58af27f28274df2) to do this, and an institution can customize their registry for their specific needs.

### Developer Environments

By way of providing "research software packages" it becomes easy to quickly spin up developer environments to try them out.
Specifically:

 - a "research software package" has both metadata and software for a deployment
 - a tool can be used to assemble a request and prepare a developer environment.
 - given that projects are extracted to a unique namespace (e.g., under a custom $HOME or /opt) we can install more than one.
 
#### Research Software Packages

By way of including multiple "blobs" as layers in a manifest, we can package the following under a single namespace:

 - Metadata file about the software
 - An SBOM software bill of materials
 - An index.json that describes the remainder of the package content

We would ideally want a flexible client that knows how to do some set of checks and deployments based
on a container technology of choice, and an environment. E.g.,:

1. Find me this set of software
2. Find me an appropriate deployment vehicle (e.g. extract source code, Singularity / Docker / Podman container)
3. Do the deployment, and make it easy to reproduce.


### Deployment

Deployment comes down to pulling or otherwise deploying and making accessible the custom container,
which also comes with all of the metadata about software and dependencies, and software bill of materials (SBOMs).
I am a collaborator that wants to deploy some custom set of projects from a registry. I
click through an interface, select some number of libraries to try, and then get a development environment with them ready to go. 
If I'm an HPC admin, I'd like to be able to click click click and get modules to install on my system for my user.  
The environment might have some set of checks to register the software (e.g., "This software is installed on the HPC system"
or check it "We looked at the SBOM and aren't concerned about any of the dependencies"). 


## Strategies

There are two general strategies we can take:

1. Place the burden of build and deploy on the individual project, meaning they can add a workflow file and token (after logging in) to authenticate their project. 
2. Provide custom builders and a registry so a webhook triggers a remote builder (akin to Singularity Hub). 

The pros of 1. are that each project is resposible for the success of their builds. The con is that we don't control them. The benefit of 2. is that we control them, but then the con is that we are responsible for them. Also, with a custom registry we can implement mostly anything we think of (e.g., custom builders).


### Project Builds on GitHub

This workflow looks like the follow.

1. The user logs in (registers) once with research-software.io (or the registry location).
2. We will need a way to authenticate a specific repository to the registry. It could be a deploy token to the repository, or an app integration.
3. The registry will either have an app that can submit a PR to add the workflow, or provide it for the user.
4. The workflow should be customized to build the software in an appropriate way (e.g., spack vs. python vs go) and save all outputs to a small filesystem "view" into a tarball (we can use oras for this).
5. The post-build step will include metadata extraction (e.g., dependencies or similar with citelang) along with sbom and manifest generation.
  - the manifest for a package includes several layers, one for metadata, one for software bill of materials, and the others the actual software.
  - we also save stars and contributor metadata with each build, so we know what the community looks like at the time of the build.
6. The packages will be pushed, and the references sent to the registry service.
7. Once the reference is added to the registry, the database is updated (to update metadata / references) and the software is available for install to a custom container.


### Deliverables

Or specific tools that are needed here.

1. A GitHub app or server that provides a service to login, connect, and interact - the "Research Software Registry"
2. A library that uses the registry API to build custom containers from packages based on manager.
3. The same library to assemble oras artifacts for a new build (push)
4. GitHub workflows and actions that use the library to build and deploy.


I think having the services based around known OCI registries and build services (e.g., GitHub packages and CI) while
it removes our control of building, is better because it will be easier for an organization to deploy their own
registry and not also need to deploy a full OCI registry and builder service.

### Goals Achieved

#### Understanding who in the group uses the software

When people request custom developer environments, each request we will keep track of what they ask for. This is a better
metric than downloads because people will request the environment specifically for development. We can also keep track of when someone requests a citation. Hopefully those two numbers would be correlated (but they don't have to be). It would be interesting to see when they are not.

#### Asking for help

Each research software entry would link directly to the GitHub (or other version control) issues board to ask for help, and documentation.

#### Understanding what software was used in a journal

If we could have the ability to "freeze" an artifact and entry, there is no reason a journal couldn't link to it as a "sort of" DOI, however this isn't as hardened as actual DOI services and I generally wouldn't promise anything. I don't even think those services that do promise things really can - how can anyone know what the world will look like in 50 or 100 years? How can we be sure some company or DOI service will still be around? We can't, so we do our best. I also have the opinion that software is a living entity, and the most useful software
will live on (survive) and the less useful software not being around forever isn't so bad. It's noise if
nobody thinks it's useful and it takes up space.

#### Code Standards

Optionally, each registry can have some kind of review process before adding a repository. E.g., they might
ask for documentation, more commenting, tests, etc. Ideally there is a standard and a clear way to follow it.

#### Exporting a Citation

If the repository has a CITATION.cff, we can use that. Otherwise we can use some set of GitHub metadata to
allow for creation of a citation via the registry interface.

#### Developer Environment Builder

Although we will provide an interface to generate custom builds from the registry, arguably the
underlying software that knows how to use a registry API to do this can be used in other contexts,
e.g., for workflows or similar.

### Futher Integrations

 - Once they have the container and have made changes, we will want to be able to save changes on demand (syspack) and move elsewhere.
  
