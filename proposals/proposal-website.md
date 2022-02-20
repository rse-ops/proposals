_Collaborative Working_

This is a proposal to make a website that will make it easy to colloborate on proposals! This means:

1. New pull requests open on the repository are considered proposals in `proposals`
2. A new proposal will trigger a workflow to add the draft to the web interface
3. Merging a pull request will add the draft as a final in progress state, in which case it can be worked on further via PR.

## Use Cases

I am hosting an initiative, project, or community that is proposal driven, and I want an easy way to maintain an interface of final
proposals and drafts. I can use this template to support this functionality.


## Sections

It's up to me how to organize my proposals, but most commuities follow some kind of template.
As the example here, we focus on a summary, use cases, and then deliverables.

## Deliverables

The deliverables for this proposal include:

 1. A web interface that can be deployed with a dispatch event (an automated event triggered by someone)
 2. on PR open, update file on gh-pages with draft state
 3. on PR close, if file not already in main, remove from gh-pages
 4. on PR merge, also update file on gh-pages with inprogress state

Opportunities for extension include supporting other templates or different kinds of interaction.

## Collaborations

* Research Software Engineers
* Web Developers

## Needs

We will need a GitHub repository with support for running workflows to enable this.