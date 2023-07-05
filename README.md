
---

# Known Issues

## GitHub Actions does automatically disable all workflow scripts after a period of time of inactivity

* Last known period: 60 days

For example, if GitHub repository has workflow scripts and was inactive a period of time, then all workflow scripts does disable.
You have to either make a commit to update the period and reenable the workflow scripts manually.

https://stackoverflow.com/questions/67184368/prevent-scheduled-github-actions-from-becoming-disabled

## `git fetch` error: `could not read Username for 'https://github.com': terminal prompts disabled`

```
Fetching the repository
  /usr/bin/git -c protocol.version=2 fetch --no-tags --prune --progress --no-recurse-submodules --depth=1 origin +refs/heads/master*:refs/remotes/origin/master* +refs/tags/master*:refs/tags/master*
  Error: fatal: could not read Username for 'https://github.com': terminal prompts disabled
  The process '/usr/bin/git' failed with exit code 128
  Waiting 14 seconds before trying again
```

Variants:

* You missed to update the repo `secrets` token.

## `git fetch` error: `The process '/usr/bin/git' failed with exit code 1`

```
Fetching the repository
  /usr/bin/git -c protocol.version=2 fetch --no-tags --prune --progress --no-recurse-submodules --depth=1 origin +refs/heads/master*:refs/remotes/origin/master* +refs/tags/master*:refs/tags/master*
  The process '/usr/bin/git' failed with exit code 1
```

Variants:

* The checkout performs on an empty repository:
  https://github.com/actions/checkout/issues/746

## The GitHub composite action has supported not all features of a generic GitHub action: https://github.com/actions/runner/issues/646

> **What does Composite Run Steps Not Support**
>
> We don't support setting conditionals, continue-on-error, timeout-minutes, "uses", and secrets on individual steps within a composite action right now.
>
> (Note: we do support these attributes being set in workflows for a step that uses a composite run steps action)

## Cygwin error: `Error: open /tmp/tmp.XXXXXXXXXX/...: The system cannot find the path specified.`

Variants:

* You have had try to run not Cygwin executable from the Cygwin shell. The Cygwin does not convert a posix path into the Windows path automatically.

  To workaround the error do use the `TEMP_DIR` variable to declare explicit temporary directory out of Cygwin `/tmp` directory.

## Linux error: `Error: open /tmp/...: no such file or directory`

Variants:

* You have had try to run `yq` from https://github.com/mikefarah/yq.

  Related issue:

  * `yq fails to process files in /tmp` : https://github.com/mikefarah/yq/discussions/1299

  To workaround the error do use the `TEMP_DIR` variable to declare explicit temporary directory out of Cygwin `/tmp` directory.

# Last known issues updates

## Updates on composite actions features

* `add conditional execution of action steps`: https://github.com/actions/runner/issues/834

  * https://github.blog/changelog/2021-11-09-github-actions-conditional-execution-of-steps-in-actions/

    Actions written in YAML, also known as composite actions, now support if conditionals.

* `Add ability to use continue-on-error from composite Action steps`: https://github.com/actions/runner/issues/1457

* `unable to inject shell to composite action`: https://github.com/actions/runner/issues/835

* `Boolean inputs are not actually booleans` : https://github.com/actions/runner/issues/1483
