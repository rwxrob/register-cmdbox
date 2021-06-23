# 🍱 CmdBox Central Command Register

Here's where you explicitly publish your CmdBox command module to the
world. For now, you can simply add your command module to the
[manifest](manifest) and submit a PR. That's it. We'll do the rest.
Everything about your module can be derived from it. The GitHub PR
process allows moderators to make sure only working, current command
modules make it into the list.

Do *not* submit placeholders or unfinished modules. Simple and silly
modules are fine. Unfinished ones are not. Abuse of this project policy
could result in blacklisting and automatic PR and detection rejection.

## Simple Space-Delimited Manifest

The plan is to follow a GitOps approach and make the
[`manifest`](manifest) file the authoritative source for all registered
or discovered command modules. (Even 10k entries would be under one
MiB.) This file can also be fetched directly (and always will be
available) from `cmdbox.sh/manifest`.

```
curl -LO cmdbox.sh/manifest
```

The `manifest` is a simple single-space-delimited table file with the
first field the name of the command and the second the Go-importable
URL. Developers are encouraged to implement caching into whatever tools
they create that fetch this file (which is only updated once a day).

## Monitored Git Hosting Providers

Eventually, this project will contain the code for automatically
discovering command modules by looking for anything beginning with
`cmdbox-` hosted on any of the monitored Git providers. Here are the git
hosts we plan to monitor (open an issue if we missed one):

Provider|URL
:-:|-
GitHub|<https://github.com>
GitLab|<https://gitlab.com>
Sourcehut|<https://sr.ht>
Bitbucket|<https://bitbucket.org>

Note that when discovery is working the need for PRs will be diminished
but not removed. Some projects may choose to not follow the `cmdbox-*`
convention or be hosted on services where detection is not currently
supported.
