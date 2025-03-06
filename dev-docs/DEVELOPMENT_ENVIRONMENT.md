# CURRENTLY THIS FILE IS A PLACEHOLDER (not updated)

# Contributing to ClassicPress

ClassicPress is a volunteer-driven open source project where multiple contributors are working towards a common goal.

Please visit [Contributing to ClassicPress](https://www.classicpress.net/contributing-to-classicpress/) for more information on contributing to the ClassicPress Project.

REWORD THE FOLLOWING PARAGRAPH?
Contributions to ClassicPress Code fall into two basic categories, ClassicPress Core Code and Plugin & Theme submissions. There are differences depending on which category your contribution falls into that we will try to explain the best we can, but the community is always willing to help, just visit one of the [communication channels](#communication-channels) if you have questions or comments.

ClassicPress code is maintained on [GitHub](https://github.com/ClassicPress), so contributors should have a GitHub account and basic knowledge using Git & GitHub.

Please be sure to read the [Governance](https://www.classicpress.net/governance/) page, which includes our Code of Conduct for interactions with ClassicPress community members.

## Table of Contents

- [Communication Channels](#communication-channels)
- [ClassicPress Core Code](#classicpress-core-code)
- [PR Review Criteria](#review-criteria)
- [What to work on?](#what-to-work-on)
- [Tips for good PRs](#tips-for-good-prs)
- [Advanced Core PR Proceedures](#advanced-core-pr-proceedures)
  - [Backporting changes from WordPress](#backporting-changes-from-wordpress)
  - [Making a backport PR](#making-a-backport-pr)
  - [Tips for a good backport PR](#tips-for-a-good-backport-pr)
  - [How to review a PR](#how-to-review-a-pr)
  - [Merging PRs](#merging-prs)


- [Plugin and Theme Submissions](#plugin-and-theme-submissions)

- [Setting up a local development environment](#setting-up-a-local-development-environment)

- [Automated Tests](#automated-tests)

- [Coding Standards](#coding-standards)

- [phpUnit Tests](#phpunit-tests)



## Communication Channels

We encourage you to join and ask any questions you have about contributing.

- [Zulip](https://classicpress.zulipchat.com/register/) - great for real-time chat, posting screenshots and asking questions about anything you're stuck on, or just socializing.
- [GitHub issues](https://github.com/ClassicPress/ClassicPress/issues) - for proposing and discussing bugfixes or other improvements.
- [Forums](https://forums.classicpress.net/) - for posting questions and searching solutions. The forums are our most active community channel other than Zulip.

## ClassicPress Core Code

Core code is the main code for ClassicPress, which encompasses everything other than 3rd party Plugins and Themes. At this time, core code is held to the same standards as WordPress core code, we will go into the standards and tests later in the document, for now lets focus on the contribution process for core code, which is via GitHub PR (_Pull Requests_).

We invite all contributors to submit Pull Requests (_PRs_) that are in line with the goals and direction of the ClassicPress Project, and to discuss and review other contributors' issues and pull requests. This will help us make the most of our limited time and review all contributions quickly.

## Review Criteria

When evaluating bug fixes and other code changes in pull requests (_PRs_), we look at these things:

1. The change does not impact or is not likely to impact existing ClassicPress users.
2. The change does not break backward compatibility or effect the existing plugin and theme ecosystem.
3. The change passes our [automated coding standards and phpunit tests](#automated-tests).
4. We understand the code change or can ask questions of someone who understands and can explain it.

If your change meets all of these criteria then we will most likely accept it.

## What to work on?

If you're not sure where to start contributing, here are some ideas:

- [Set up a local development environment](#setting-up-a-local-development-environment) so you can work with ClassicPress on your own computer.
- Review [existing PRs](https://github.com/ClassicPress/ClassicPress/pulls) by looking at what they provide and how they fit the criteria described above.
- Ask the community and be involved in community discussions for ideas on how to help.
- Submit PRs based on our [planned milestones](https://github.com/ClassicPress/ClassicPress/milestones), or PRs with your own suggested changes. Remember, these will be subject to review, so please make sure they are in line with the project's direction.

## Tips for good PRs

- A good Pull Request (PR) should be for a single, specific change. The [PR Template](https://github.com/EliteStarServices/ClassicPress/blob/develop/.github/PULL_REQUEST_TEMPLATE.md) provided on GitHub can be used to explain and describe your proposed changes.
- Before submitting a PR it can be very useful to run some tests locally to save time revising your PR later. _(see [Automated tests](#automated-tests) below)_.
- It is always a good idea to look at the "Files" view on GitHub after submitting your PR to verify that the changes look as expected. Generally, there should be no "extra" changes that are not related to the purpose of your PR like reformatting or re-aligning files. Such changes are best done in a separate PR just for that purpose. If you see something that looks out of place, you can make an edit to fix it and push a new commit to your PR.
- Generally it is best to only use one pull request for each change, even if the initial code needs revision after review and feedback. Closing the initial pull request and opening a new one makes it more difficult to follow the history of the change, and it is much better to just update the existing PR in response to any feedback received.
- To be accepted, a PR **must** pass the automated tests which are run using GitHub Actions. Sometimes the tests experience unrelated failures, we will be happy to help resolve these. Usually, when this happens we start a separate PR to resolve the failure, and once that is merged, your PR will need to be updated as per the next bullet point.
- New functions, filters and actions need to be fully documented consistently with the established DocBlock format. `@since` parameters for new ClassicPress features that diverge from WordPress must be prefixed with `CP-`, for example `@since CP-2.0.0`.
- You can always refresh your PR branch against the latest ClassicPress code using the following sequence of commands:

  ```bash
  git checkout your-pr-branch
  git fetch upstream
  git merge upstream/develop
  git push origin your-pr-branch
  ```

## Advanced Core PR Proceedures

_This section describes some of the Advanced PR Proceedures._

## Backporting changes from WordPress

ClassicPress version `1.0.0` was a fork of WordPress `4.9.x`. Since then, changes have been made to ClassicPress and WordPress for performance, bugfixes and new features.

ClassicPress `2.x.x` has generally kept backward compatibility with the WordPress 4.9 branch intact. However, we have also been merging bugfixes and enhancements from later versions of WordPress.

Changes must be proposed and reviewed **individually** - long lists of tickets or changesets from individual WordPress versions don't give us what we need in order to plan and understand each change well.

If you're not sure about any of that, then it's a good idea to ask first. A good way is to create an issue for the specific change you're interested in, along with links to the relevant WordPress changesets and tickets, and any other information you have about how the change works.

## Making a Backport PR

When you're ready to backport a code change:

1. Identify the WordPress **changeset number** that you'd like to port such as `43123`.
2. Run `bin/backport-wp-commit.sh` script in your terminal/command prompt to apply the change to your code:

   ```bash
   bin/backport-wp-commit.sh CHANGESET_NUMBER
   ```

   or use composer:

   ```bash
   composer run backport CHANGESET_NUMBER
   ```

   This will create a new branch and apply the WordPress changeset to it. If you're porting multiple changesets, you can create a new `git` branch first and use the `-c` option to this script to apply each changeset to your current branch instead:

   ```bash
   bin/backport-wp-commit.sh -c CHANGESET_NUMBER
   ```

   or use composer:

   ```bash
   composer run backport -c CHANGESET_NUMBER
   ```

   Using this script for all backports saves time for you and for the maintainers. It uses a standardized format for commit messages, which makes it possible for us to track which WordPress changes we've already included.

   **Pay close attention to the output of this script** and let us know if you see anything strange or confusing!
3. Resolve merge conflicts (if any) by editing the conflicting files, running `git add` and then `git commit`. If you cannot resolve the conflicts, ask for help in the [**#core** Zulip channel](https://classicpress.zulipchat.com/register/) or just push your branch as-is and we'll take care of it!
4. Repeat steps 2 and 3 for any further WordPress changesets that are related to this PR.
5. Push your branch to your fork on GitHub using `git push origin merge/wp-rCHANGESET_NUMBER` or the name of your current branch.
6. Use the GitHub website to make a PR against the `develop` branch for review.

### Tips for a good backport PR

- Give your pull request a clear title that explains in a few words what change or feature you are backporting from WordPress.
- In the body text of the PR, explain what the specific change is, how it works and why ClassicPress in particular should adopt it.
- Often there is a lot of good discussion about each change in the relevant WordPress Trac tickets. It makes the maintainers' job much easier to see this discussion summarized and linked.
- Explain what testing has been done on your PR and what may be left to do. Screenshots and text instructions documenting the changes and how to test them are very useful. Those tell other contributors looking at the PR how to verify the changes. "This was tested in WordPress" **is not enough** to meet our review criteria, see [Review Criteria](#review-criteria) above.
- Look through the WordPress tickets and commits associated with these changes. Make sure there are no other changes to commit, no outstanding issues with the WordPress changes mentioned in Trac tickets, and summarize your findings on your PR.
- If there are merge conflicts during the backport, check if they have been resolved correctly by comparing the final changes from the full PR against the corresponding WP changeset(s). The code changes to be applied to ClassicPress should be basically the same as the code changes that were applied to WordPress.

## How to review a PR

1. See the instructions on [setting up a local development environment](#setting-up-a-local-development-environment).
2. Set up a remote link to the user who submitted the PR. For example, if GitHub user `bahiirwa` submitted the PR:

   ```bash
   git remote add bahiirwa https://github.com/bahiirwa/ClassicPress
   git fetch bahiirwa
   ```

3. Look at the PR on the GitHub web interface and note the _branch name_ that was used to submit it. For example: `bahiirwas-cool-pr`
4. Checkout of the branch with the changes you want to test using

   ```bash
   git checkout -b bahiirwas-cool-pr <name-of-remote>/bahiirwas-cool-pr
   ```

5. Run tests as the PR suggests, or stress test the PR trying to confirm whether the change works as intended.
6. Submit your feedback in the comment section of the same PR on the CP Github repo. Screenshots, gifs, video and text instructions documenting the tests are very useful to document your testing.
7. Thank you for your time and effort in helping us review PRs.

## Merging PRs

_This section only applies to **core committers** - people who have access to merge changes to ClassicPress._

See [MAINTAINING.md](MAINTAINING.md) for some guidelines for maintaining ClassicPress.


**CUT FILE HERE?**


## Plugin and Theme Submissions

**NEW SECTION**


## Setting up a local development environment

**THIS SECTION TO BE REWORKED**

1. Make sure you have [git](https://git-scm.com/), [Apache](http://httpd.apache.org/) and [MySQL](https://www.mysql.com/)/MariaDB installed and working on your computer. Installing [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/) may be useful for Windows user, for example when running `grunt` tasks (see below).
2. Fork ClassicPress to your GitHub account using the GitHub website.
3. Clone your ClassicPress fork to your computer using the following command:

   ```
   git clone https://github.com/YOUR_GITHUB_USERNAME/ClassicPress
   ```

   Run this `git clone` command from within the webroot directory of your Apache webserver, or otherwise point your webserver at the resulting directory.
4. Change to the ClassicPress repository: `cd ClassicPress`
5. Add the main ClassicPress repository so that you can pull changes from it: `git remote add upstream https://github.com/ClassicPress/ClassicPress`
6. Run `git remote -v` and confirm that you have your own fork set as `origin` and the main ClassicPress repository set as `upstream`. The rest of this document assumes you have things set up this way.
7. Create a MySQL database to connect with your CP instance.
8. In your browser, go to the `src` directory on your localhost instance of CP to run the setup. (You can also configure the `wp-config.php` file yourself instead.)
9. Use normal `git` commands to check out a branch, and you will immediately be able to see the changes from that branch in your web browser _(see [How to review a PR](#how-to-review-a-pr) below)_.

At this point you have a working local development environment. Here are some further steps for more advanced usage:

- Set up [`composer`](https://getcomposer.org/) to run and develop automated tests _(see [Automated tests](#automated-tests) below)_.
- Set up Node and `grunt` to run the pre-commit checks, make your own builds of ClassicPress, and perform other miscellaneous build and development tasks:
  - Set up [`nvm`](https://github.com/nvm-sh/nvm) or a similar program to manage Node versions.
  - Run `nvm install` or use your version manager to switch to the current version of Node and `npm` (Node package manager) used by ClassicPress. Run this step periodically.
  - Run `npm install` to install/update the ClassicPress `npm` dependencies. Run this step periodically.
  - Run `npm install -g grunt-cli` to make the grunt command line available globally. When changing Node versions, you may need to run this command again.
  - Run `grunt build` to create your own build of ClassicPress (in the `build` directory) or run `grunt precommit:verify` to test whether any other files may need to be updated for your PR. There are many other `grunt` commands available in the `Gruntfile.js` file.



## Automated Tests

**THIS SECTION TO BE UPDATED AND REWORKED**

Any change that introduces new code or changes behavior should have automated tests. These tests mostly use [PHPUnit](https://phpunit.de/) to verify the behavior of the many thousands of lines of PHP code in ClassicPress.

If you're not familiar with automated tests, the concept is basically **code that runs other code** and verifies its behavior.

Documentation for running and updating our existing tests, as well as the code for the tests themselves, can be found in the [`tests/phpunit`](../tests/phpunit) subdirectory of this repository.

[`Composer`](https://getcomposer.org/) can be used locally to run unit tests,
- `composer run phpcs` - checks coding standards on source files
- `composer run phpcs-tests` - checks coding standards on test files
- `composer run phpunit` - runs unit tests

QUnit is used for testing JavaScript and these tests can be run in a browser at the local path `tests/qunit/index.html` or from the command line with `grunt qunit:local`.


## Coding Standards

**NEW SECTION / CORE & ADD-ON**

## phpUnit Tests

**NEW SECTION**


### Link Definition Testing

[url1]: https://elite-star-services.com
[url2]: https://classicpress.net

[ESS][url1]
[ClassicPress][url2]