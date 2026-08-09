# InfraTools

Infrastructure tools packaged for distribution via MungerWare's APT repository
(`MungerWare/apt-packages`). Each tool lives in its own directory as a raw
dpkg tree (`DEBIAN/control` + install paths), built into a `.deb` and pushed
to the apt repo by CI on every push to `main`.

| Tool | Description |
|------|-------------|
| `ipmifanctl` | IPMI fan control |
| `mw-pxeboot` | Set next boot to PXE and reboot |
| `ocsessnotify` | Post notifications to the most recent opencode session |
| `perccli` | Dell PERC CLI (vendored binary) |

## Publishing

Pushing to `main` triggers `.github/workflows/publish.yml`, which builds every
package directory into a `.deb` and pushes them to the `pool/` of
`MungerWare/apt-packages`. The apt repo's own CI then regenerates the dists
indexes and serves `apt.mungerware.com`.

Requires the `APT_REPO_TOKEN` secret (SSH deploy key with push access to
`MungerWare/apt-packages`).
