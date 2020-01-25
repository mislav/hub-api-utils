# `hub api` utils

This is a collection of small utility scripts to showcase examples of automating
GitHub tasks from the command-line via the [`hub api`](https://hub.github.com/hub-api.1.html)
command.

Some available commands are:

* [hub-comment](./bin/hub-comment) - post a comment to an issue/PR
* [hub-pr-merge](./bin/hub-pr-merge) - The Merge Button™ on the command-line
* [hub-pr-with-commit](./bin/hub-pr-with-commit) - find the PR which originated a commit
* [hub-repo-rename](./bin/hub-repo-rename) - rename the current repo

Prerequisites:

* [hub 2.12+](https://github.com/github/hub/releases)
* git 1.8+
* bash (for many scripts)
* [jq](https://stedolan.github.io/jq/) (for some scripts)
* standard POSIX tools such as `grep`, `awk`, `sed`

Installation with Homebrew:

```
brew install hub jq
```

Then drop individual scripts from this repo into your $PATH and edit them or use
them as you see fit.

## How to contribute

I would love to accept your scripts into this repository! Please send your pull
requests. The prerequisites for submission are simple:

- Your script should do something useful or interesting with the GitHub API
  using the `hub api` command. Either REST or GraphQL APIs might be used.

- The script should be written in one of the widespread shells such as `bash` or
  `zsh`, or in often-available interpreted languages such as `ruby`, `node`, or
  `python`.

- When shelling out to other commands, please try to stick to `jq` and the POSIX
  set of command-line utilities to keep scripts portable.

- There are no other rules. Go wild! But please note that when you do submit
  contributions to this repository, you are releasing your code into the public
  domain per [LICENSE](./LICENSE).

## Tips for `hub api`

The GitHub REST API can be queried like so:

```sh
# The placeholders "{owner}" and "{repo}" get populated with values from the
# current git repository:
hub api 'repos/{owner}/{repo}/issues'
```

The response is always JSON, which can be parsed using `jq` in shell scripts.
Alternatively, you may specify the `--flat` flag to have `hub api` output data
in a line-based format.

The GraphQL API can be queried like this:

```sh
hub api graphql -f query='QUERY'
```

For more information/examples, see https://hub.github.com/hub-api.1.html.
