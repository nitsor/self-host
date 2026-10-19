# Nitsor self-host

Release bundles for running Nitsor on your own server with Docker Compose.

**Backend preview.** A bundle installs the Nitsor backend and the Convex
operator dashboard on one host. It does not include the Nitsor web app yet, so
there is no Nitsor sign-in page to open.

## Requirements

- An arm64 or x86_64 Linux or macOS host.
- Docker Engine or Docker Desktop with the Compose v2 plugin.
- 10 GiB of free disk.
- Free TCP ports 3210, 3211 and 6791 on 127.0.0.1.
- An OIDC client registered with your identity provider: its issuer URL,
  client ID and client secret.
- `minisign`, and `sha256sum` or `shasum`, to verify the download.

## Download

From [Releases](https://github.com/nitsor/self-host/releases), download the
three files of the latest release: `nitsor-self-host-<release>.tar.gz`,
`SHA256SUMS` and `SHA256SUMS.minisig`.

## Verify

Every release is signed with the Nitsor release key, ID `F1819173358F3BE4`.
Its public key is [`release-minisign.pub`](release-minisign.pub):

```text
RWTkO481c5GB8bmLTl8iwbOpSAR67EFs0OoVz3LrRmoPKLA2oXd2WH09
```

In the directory that holds the three files, check the signature, then the
tarball:

```sh
minisign -Vm SHA256SUMS -P RWTkO481c5GB8bmLTl8iwbOpSAR67EFs0OoVz3LrRmoPKLA2oXd2WH09
sha256sum -c SHA256SUMS
```

With a copy of `release-minisign.pub` from this repository, the first command
can be `minisign -Vm SHA256SUMS -p release-minisign.pub`. On macOS, use
`shasum -a 256 -c SHA256SUMS` for the second. Install only when both succeed.
The trusted comment minisign prints names the release version and the source
commit, which `release.txt` in the bundle also records.

## Install

```sh
tar -xzf nitsor-self-host-<release>.tar.gz
cd nitsor-self-host
./install.sh
docker compose -f compose.yaml up -d
```

`install.sh` checks the bundle and the host, asks for the OIDC issuer URL,
client ID and client secret, writes `.env` with mode 600, pulls the pinned
images and deploys the Nitsor functions. The last command starts Nitsor.
Back up `.env`: its `INSTANCE_SECRET` is the only key to this installation's
data. The `README.md` inside the bundle covers unattended installs, the
installer's checks and what runs on each port.

## Upgrade

1. Download and verify the new release as above.
2. In the directory that holds `nitsor-self-host`, unpack the new tarball over
   it. The bundle has no `.env`, so yours is kept.
3. In `nitsor-self-host`, run `./install.sh`, then
   `docker compose -f compose.yaml up -d`.

Downgrades are unsupported. `install.sh` refuses a bundle built more than 30
days ago unless you run it with `--allow-stale`.

## Questions and issues

Issues are turned off in this repository. For questions and bug reports,
contact us through [nitsor.com/contact](https://nitsor.com/contact). Report
security problems privately through the same page, never in public.
