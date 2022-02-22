## Proposals

**⭐️ Welcome to Special Projects Proposals! ⭐️**

This is a collaborative space for working on proposals for rse-ops.

1. New pull requests open on the repository are considered in-review proposals.
2. If you open a pull request that already has a PR for a proposal open it will not be allowed.
3. A new or updated proposal will trigger a workflow to add the in-review draft to the web interface.
4. Merging a pull request will approve the draft as "graduated."
5. Add a label prefixed with `status-` to a pull request to give it a different label (e.g., `status-incubating` or `status-paused`).

And if you want to work on an incubating proposal further, just open a pull request! This repository is based on
[proposal-jekyll](https://github.com/vsoch/proposal-jekyll) in case you want to make your own version.

### Usage

#### How do I add a new proposal?

To submit a proposal, you will open a pull request to the repository. 

1. The markdown file should be added under [proposals](https://github.com/rse-ops/proposals/tree/main/proposals) at the top level.
2. The name of the file should correspond to the title, e.g., "Automated Container Builds" should be `proposals/automated-container-builds.md`. Only lowercase letters, numbers, and `-` are allowed in the name.
3. You should not write the title in the document - it will be added by the automation.
4. You should not add any front end matter, as it will be automatically added.

Once you've prepared the markdown file, open a pull request to the repository, and the proposal
will be labeled as `in-review`. When it's ready to be graduated or paused, a maintainer will add a label
to the pull request for either:

 - `status-graduated`
 - `status-paused`
 
You aren't allowed to open pull requests to edit more than one proposal at a time.

#### How do I update an existing proposal?

All proposals live in [proposals](proposals) on the main branch. When you want to edit
an existing one, simply make changes and open another pull request. By way of having
the same filename, the proposal on the site will be updated to return to an in-review state.
While you are working on the draft, the previous approved proposal (if applicable)
will not be touched. The reason is because if you close the pull request we wouldn't
want to alter or remove it.

#### How do I delete a proposal?

To delete a proposal, simple open a pull request to delete the file
from the main branch. For the sake of caution it won't be deleted on the PR, but when it is merged
into main. You can also ask the maintainer to manually delete the file
from the branch in the UI, which might be easier.

#### What happens if close a pull request?

If your pull request created a draft, we delete the draft. We do not
delete and previously approved version of the proposal.

#### What happens if two pull requests are working on the same file?

By default, we are only allowed one draft in progress at once. If you open
a pull request and the draft is being worked on somewhere else,
the PR will fail. You should thus check before you open a PR that there
isn't already a draft in progress!


License
-------

Copyright (c) 2017-2021, Lawrence Livermore National Security, LLC. 
Produced at the Lawrence Livermore National Laboratory.

RADIUSS Docker is licensed under the MIT license [LICENSE](./LICENSE).

Copyrights and patents in the RADIUSS Docker project are retained by
contributors. No copyright assignment is required to contribute to RADIUSS
Docker.

This work was produced under the auspices of the U.S. Department of
Energy by Lawrence Livermore National Laboratory under Contract
DE-AC52-07NA27344.
