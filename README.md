# dramatis-releases

Public distribution point for the Dramatis platform: signed backend
release artifacts and the sanitized NixOS configuration snapshot.

This repo contains **build artifacts only — no source code**.

## Verifying a release

All `charplatform-server-*.tar.xz` artifacts are signed with minisign.
The public key (verification material, not a secret):

```
untrusted comment: minisign public key 05A62671B9C2ABC6
RWTGq8K5cSamBY8uPPUP70dfelSjmi+5q4yvynK+yLuj4QR1so8MRAah
```

Verify before use:

```sh
minisign -Vm charplatform-server-<version>-x86_64-linux.tar.xz \
  -P RWTGq8K5cSamBY8uPPUP70dfelSjmi+5q4yvynK+yLuj4QR1so8MRAah
```

The NixOS configuration pins both the artifact hash (SRI) and the
signature hash, and refuses to install any tarball that contains
source files.
