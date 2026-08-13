# nova-catalog

The master app list for the Nova Network toolset, consumed by
[nova-updater](https://github.com/nv-core/nova-updater). Register it once per
machine:

```bash
nova catalog add https://github.com/nv-core/nova-catalog.git
```

nova syncs this repo before every check/update, so managing the fleet is just
git: **add a tool** = add its URL to [apps.list](apps.list) and commit;
**pin/rollback a version** = append `ref=<tag>`; **remove a tool** = delete
the line (installed copies stay until uninstalled). Local `apps.list` entries
on a machine always win over catalog entries.

Entry options: `branch=<name>`, `ref=<tag>`, `scope=system` (root apps —
requires the machine to have run `install.sh install --with-system`).

The catalog itself always follows HEAD — no tags needed here.
