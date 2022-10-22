# Contributing

Read our [Code Of Conduct](https://github.com/unixorn/hass-postgresql-backup/blob/main/Code_Of_Conduct.md). TLDR; Don't be a jerk. If that's a problem for you, I don't mind not getting your contributions.

## Contribution Guidelines

- **To add a helper script:** Submit a pull request.
  - Please use `#!/usr/bin/env interpreter` instead of a direct path to the interpreter, this makes it easier for people to use more recent interpreter versions when the ones packaged with their OS (macOS and CentOS, I'm looking at you) are stale.
  - Please _do not_ include a language file extension in the script name unless they are meant to be sourced and not run standalone. No one should have to know if a script was written in bash, python, ruby or whatever language to use a script. Not including file extensions makes it easier to rewrite the script in another language later without having to change every reference to the previous version.
