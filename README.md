# Server Sanctuary: release downloads

Server Sanctuary is a terminal UI for hosting game servers on your own Linux machine, each as a
rootless Podman container run by a systemd user service.

This repository holds release binaries only. The source is private.

## Download

The program for this machine (`x86_64`, or `aarch64` for 64-bit ARM), the checksums and their
signature, from the latest release:

```sh
asset="server_sanctuary-$(uname -m)-linux-gnu"
base=https://github.com/tossbaws/server-sanctuary-releases/releases/latest/download
curl -LO "$base/$asset"
curl -LO "$base/SHA256SUMS"
curl -LO "$base/SHA256SUMS.minisig"
```

- The program for x86_64: https://github.com/tossbaws/server-sanctuary-releases/releases/latest/download/server_sanctuary-x86_64-linux-gnu
- The program for aarch64: https://github.com/tossbaws/server-sanctuary-releases/releases/latest/download/server_sanctuary-aarch64-linux-gnu
- The checksums: https://github.com/tossbaws/server-sanctuary-releases/releases/latest/download/SHA256SUMS

Every release, with its notes: https://github.com/tossbaws/server-sanctuary-releases/releases

## Verify and run

In the folder holding the downloads, check the signature first (see below), then:

```sh
sha256sum -c --ignore-missing SHA256SUMS
chmod +x "$asset"
./"$asset" --version
```

`sha256sum -c` must say `OK`. With no arguments the program starts the terminal UI.

### Verifying a download

Releases are signed with [minisign](https://jedisct1.github.io/minisign/). The public key, key ID `0814E53E32EAC1E1`:

    untrusted comment: minisign public key 0814E53E32EAC1E1
    RWThweoyPuUUCC7h9W/6n+qHzga95k3Lxzi6kCqVoO747X+/lr3usXT+

Save those two lines as `minisign.pub`, download `SHA256SUMS` and `SHA256SUMS.minisig` beside the binary, and in that folder run:

    minisign -Vm SHA256SUMS -p minisign.pub
    sha256sum -c --ignore-missing SHA256SUMS

Each binary also has its own signature (`server_sanctuary-x86_64-linux-gnu.minisig`, `server_sanctuary-aarch64-linux-gnu.minisig`). Get minisign with `sudo apt-get install minisign` (Ubuntu 24.04+), or from https://github.com/jedisct1/minisign/releases.

## Requirements

- Linux on x86_64 or aarch64 (64-bit ARM) with glibc 2.35 or newer, such as Ubuntu 22.04 or newer
- Rootless Podman
- systemd, with a user session and linger enabled for your user
- On ARM, Valheim can't be deployed: its server image has no ARM build. The ARM build has not
  yet run on real ARM hardware.

## Licences

Free needs no key and runs 2 servers per machine. Keys for more servers and the Pro features are
at https://buy.polar.sh/polar_cl_F0kOFDoRjx7pKEZgTxLe0WZ0VlNEDS1MqiqPF0yNdQF.

Terms: https://tossbaws.github.io/chirhocode-site/terms/

## Support

help@chirhocode.com. This repository has no issue tracker: please send questions and bug reports
to that address.

All rights reserved, Chi Rho Code LLC; use is governed by the terms.
