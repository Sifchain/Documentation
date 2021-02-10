# Contributing to Sifchain

## Philosophy

TODO add Engineering Guidelines..

## Development Standards

Sifchain uses Gitflow to handle development.  Gitflow is described in more detail [here](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow#:~:text=Gitflow%20Workflow%20is%20a%20Git,designed%20around%20the%20project%20release.&text=In%20addition%20to%20feature%20branches,%2C%20maintaining%2C%20and%20recording%20releases).  You can easily download a Gitflow plugin for your local development environment or personal cloud. 

1. Developer begins a new feature by forking \`develop\` and creating a new branch labeled \`feature/add-x.\`  This new branch has an analogous cloud environment created for it where the developer can deploy their own private blockchain to develop and test this feature
   1. Developers frequently rebase code from \`develop\` into their \`feature/add-x\` branch to ensure their code operates properly with other people’s pull requests \(PRs\).  
   2. Developer ensures all tests from everyone’s code pass before creating a pull request to merge \`feature/add-x\` into \`develop\`
      1. \`develop\` has branch protection \(as does \`master\`\) to ensure that all pull requests to that branch pass a code review prior to being merged in
         1. A developer will never run \`git push -f\` on \`develop\` or \`master\`
      2. Code reviewers can take no more than 48 hours to review any new PR on which they are tagged.  Even more frequent reviews are requested if possible
         1. An Sifchain team member should be tagged on every PR from \`feature/add-x\` to \`develop\`
            1. A code-related PR can be merged from \`feature/add-x\` to \`develop\` without explicit approval from an executive if the other reviewers come to consensus on supporting it
               1. 1. Reviewers can reject code for issues related to performance and security, but not coding style
            2. An architecture-only PR cannot be merged from \`feature/add-x\` to \`develop\` without explicit approval from an executive
      3. Developer attains at least 50% test coverage for the feature he has developed and is merging in
2. After code review passes, the developer merges code into \`develop.\`  From here, it is deployed to a public testnet.
   1. Sifchain’s internal testing team will increase the test coverage from 50% to at least 90% and will run through a series of end-to-end or complex situational tests both isolated to Sifchain’s testnet and involving the testnets of other, related networks.  The internal testing team will also test the effects of arbitrary components of infrastructure failure on the feature to mitigate harm or lost funds to the end user in the case of hardware attacks or other attacks on the infrastructure of the internet upon which Sifchain relies.
   2. External testing teams will try to identify bugs, fault tolerance issues, or other concerns with varying levels of coordination with Sifchain.  Some of them will be directly paid by the Sifchain core team on a regular basis.  Others will be compensated by the Sifchain core team or SifDAO for bounties on specific issues.
   3. Validators will run the testnet to ensure that it can be practically used under regular circumstances.
   4. Integration partners will engage with the testnet to set up new test features for their products, making it easy to go live
   5. The Sifchain and broader cryptocurrency community will test the blockchain infrastructure to assess its quality and evaluate using it with their own portfolio or product integrations
3. After 1 to 2 weeks of testing on the testnet, the feature in \`develop\` \(which at this part of the process is running on the testnet\) will be merged into \`master\` \(which runs on mainnet\)
   1. All PRs that merged from \`develop\` to \`master\` require the approval of at least one executive. 
4.  When reporting bugs make sure to attach relevant information such as bug reproduction steps as well as evidence along with other details as mentioned in this template [**https://github.com/Sifchain/sifnode/blob/develop/.github/ISSUE\_TEMPLATE/bug\_report.md**](https://github.com/Sifchain/sifnode/blob/develop/.github/ISSUE_TEMPLATE/bug_report.md)

## Preparing Code for Review

Preparation sets your reviewers up for success.

#### Commit Messages

Make sure your commit messages are descriptive.

#### Github PR Descriptions

Your PR descriptions should be an extension of your commit messages. Write about both what the commit changes, and how you implemented the change.

## Performing Code Reviews

#### How to Review

* Make two passes over the PR if it's substantial.
  * On the first pass, come to an understanding of the code change at a high level.
  * On the second pass, pay more attention to semantic details.

#### Making Code Changes

* Test PRs rigorously before requesting review.
* Include test cases you've checked for in your PR description.

#### Reviewing Code

* If the change is substantial and user-facing, pull down the branch.
* Test for cases \(particularly edge cases\) that the PR author may have missed.

#### QA

* Look at the list of items going out for release the next day.
* Go down the list one-by-one and thoroughly test changes.

