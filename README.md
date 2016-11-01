# What is acces.sh?

This provides a very simple way to fetch public keys and generate an
`authorized_keys` file. The motivation came from wanting to give my GitHub
Team access to servers automatically by grabbing their public keys from
their profiles.

Currently, we have support for GitHub teams, however, I would like to support
other services (such as GitLab).

## Dependencies

* [jq](https://stedolan.github.io/jq/download/)

## Usage
[Generate a token](https://github.com/settings/tokens) and be sure to give it the permission `read:org`
> Read org and team membership

`./acces.sh --gh-token TOKEN --gh-org ORG --gh-team TEAM`

By default, we write to `/tmp/authorized_keys`; however, you can override it with `--keyfile /path/to/authorized_keys`

## Security Risks
Since we by default create a file at `/tmp/authorized_keys`, this poses a
potential security threat on multi-user servers. See [#2](https://github.com/FatBoyXPC/acces.sh/issues/2)
for more information.

## Alternatives
We found a few packages to solve this problem, but we were looking for something
with simpler dependencies.

* https://github.com/stackbuilders/openssh-github-keys
* https://github.com/trevoro/sshauth
* https://github.com/spoqa/geofront
