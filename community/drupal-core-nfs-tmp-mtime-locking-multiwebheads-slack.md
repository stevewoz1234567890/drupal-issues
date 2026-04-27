# NFS, multi web heads, compiled containers, `/tmp`, locking, and `MTimeProtectedFileStorage` (Slack)

**Context:** A Slack thread started from Docker Compose work to exercise **NFS** mounts and shared storage of compiled **DI container** files across several **web heads**. Default **NFS** client caching (`ac` / `actimeo`) raced with mtime-sensitive protected file storage. Stricter mount flags (e.g. `lookupcache=none`, `actimeo=0`) helped tests but are not portable to every host. The thread covered file-based locking, per-node system temp for rebuildable artefacts, Symfony’s kernel container lock pattern, and security review of [`MTimeProtectedFileStorage`](https://api.drupal.org/api/drupal/core%21lib%21Drupal%21Component%21PhpStorage%21MTimeProtectedFileStorage.php/class/MTimeProtectedFileStorage/11.x) after **dww** raised deserialization and `touch` / mtime concerns.

## Takeaways

- **alexpott / berdir:** lock file; avoid unguarded parallel writes into a shared cache directory on **NFS**.
- **longwave:** NFS is not a cluster-wide coherent cache; defaults refresh attributes on a ~seconds cadence. `noac` / `actimeo=0` improve correctness at a performance cost. If the built container is keyed by a stable hash, each web node can materialize its own copy under local `/tmp` and skip **shared** storage for that blob.
- **Symfony:** See [`KernelTrait` (8.1, ~L120–263)](https://github.com/symfony/symfony/blob/8.1/src/Symfony/Component/DependencyInjection/Kernel/KernelTrait.php#L120-L263) for fast path, read lock + wait, write lock when building.
- **Per-host `/tmp`:** **catch** — GC is messy but fine for ephemeral blobs; load balancing eventually touches each node. **alexpott** / **berdir** note compiled Twig in tmp can grow in volume; not the same footprint as a single small container file.
- **Multi-process on one node:** **alexpott** — you still need locks without **NFS**; same class of issue as **Symfony** addresses.
- **Security (dww / catch):** **dww** asked about deserializing from `/tmp`. **catch** pointed at `MTimeProtectedFileStorage` and the existing pattern of PHP-on-disk (compiled Twig, etc.); **dww** still wanted a concrete review of mtime / `touch` — read the [class](https://api.drupal.org/api/drupal/core%21lib%21Drupal%21Component%21PhpStorage%21MTimeProtectedFileStorage.php/class/MTimeProtectedFileStorage/11.x), not this summary.
- **Implementation:** **alexpott** posted a **core** MR (system temp + locking for multiple web heads) — look up the active MR for status.
- **Repro:** [**alexpott/multiwebheads**](https://github.com/alexpott/multiwebheads) on GitHub.

## Use

- **SRE / PaaS:** NFS-backed mutable PHP caches need an explicit coherence strategy (locks, per-node storage, or stricter mounts), not “POSIX is enough.”
- **Core review (related MR):** weigh **catch**’s latency note — container build can be hundreds of ms while observing a lock is tens of ms — when arguing for read-lock / wait during build.
- **Threat modelling (dww’s thread):** re-read `MTimeProtectedFileStorage` invariants if container output moves to new paths such as `/tmp` or files.
