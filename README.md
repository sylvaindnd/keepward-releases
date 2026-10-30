# Keepward releases

Signed release files of the Keepward agent. The source code is not public: this
repository only holds what a server downloads.

Each release has these files:

| File | Content |
|---|---|
| `keepward-agent-x86_64` | Agent, static binary for x86_64 Linux |
| `keepward-agent-aarch64` | Agent, static binary for arm64 Linux |
| `keepward-agent.service` | systemd unit of the agent |
| `keepward-jobs.slice` | systemd slice for the agent's heavy jobs |
| `install.sh` | Installer for Debian 13 |
| `SHA256SUMS` | SHA-256 checksums of all the files above |

Every file, `SHA256SUMS` included, has a minisign signature next to it
(`<file>.minisig`). Its trusted comment is `keepward-agent v<version> <file>`.

## Verify a release

You need [minisign](https://jedisct1.github.io/minisign/) and the release public key
(below).

```sh
minisign -Vm SHA256SUMS -P <public key>
sha256sum -c SHA256SUMS
```

`install.sh` does the same checks before it installs anything, with the public key
written in it. The agent checks its updates with the public key compiled into it.

## Release public key

```
<added with the first release>
```
