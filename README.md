# Server Sanctuary: release downloads

Server Sanctuary is a terminal UI for hosting game servers on your own Linux machine, each as a
rootless Podman container run by a systemd user service.

This repository holds release binaries only. The source is private.

## Download

- The program: https://github.com/tossbaws/server-sanctuary-releases/releases/latest/download/server_sanctuary-x86_64-linux-gnu
- Its checksum: https://github.com/tossbaws/server-sanctuary-releases/releases/latest/download/SHA256SUMS

Every release, with its notes: https://github.com/tossbaws/server-sanctuary-releases/releases

## Verify and run

In the folder holding both files:

```sh
sha256sum -c SHA256SUMS
chmod +x server_sanctuary-x86_64-linux-gnu
./server_sanctuary-x86_64-linux-gnu --version
```

`sha256sum -c` must say `OK`. With no arguments the program starts the terminal UI.

## Requirements

- Linux on x86_64 with glibc 2.35 or newer, such as Ubuntu 22.04 or newer
- Rootless Podman
- systemd, with a user session and linger enabled for your user

## Licences

Free needs no key and runs 2 servers per machine. Keys for more servers and the Pro features are
at https://buy.polar.sh/polar_cl_4XRKscuORd3FVcX10BSYWjPDeL9ffNwIgzMmn4Paoej.

Terms: https://tossbaws.github.io/chirhocode-site/terms/

## Support

help@chirhocode.com. This repository has no issue tracker: please send questions and bug reports
to that address.

All rights reserved, Chi Rho Code LLC; use is governed by the terms.
