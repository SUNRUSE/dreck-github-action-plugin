# Dreck GitHub Action Plugin [![License](https://img.shields.io/github/license/sunruse/dreck-github-action-plugin.svg)](https://github.com/sunruse/dreck-github-action-plugin/blob/master/license) [![Renovate enabled](https://img.shields.io/badge/renovate-enabled-brightgreen.svg)](https://renovatebot.com/)

Configures a project built using Dreck to automatically run in continuous integration as a GitHub Action.

## Installation

Run the following in a Bash shell at the root of your project:

```bash
git submodule add https://github.com/sunruse/dreck-github-action-plugin submodules/plugins/github-action
make --file ./submodules/dreck/makefile
```

Other plugins you install will most likely have their own dependencies (e.g. NodeJS) which are not automatically taken into account by this plugin.  You will need to modify the [.github/workflows/continuous-integration.yaml](./bundled/.github/workflows/continuous-integration.yaml) file it generates to install these before the Dreck makefile is executed.

## Build outputs

The default behavior of this plugin is to discard build outputs for normal commits on branches or in raised PRs - the build is performed merely to ensure that it _can_ be completed successfully.

It will, however, also run when a GitHub release is created.  Following a successful build, all files in the `./dist` directory and its subdirectories are added to the release.
