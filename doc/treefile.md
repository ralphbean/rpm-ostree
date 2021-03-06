Treefile
--------

 * `ref`: string, mandatory: Holds a string which will be the name of
   the branch for the content.

 * `gpg_key` string, optional: Key ID for GPG signing; the secret key
   must be in the home directory of the building user.  Defaults to
   none.

 * `repos` array of strings, mandatory: Names of yum repositories to
   use, from the system `/etc/yum.repos.d`.

 * `selinux`: boolean, optional: Defaults to `true`.  If `false`, then
   no SELinux labeling will be performed on the server side.

 * `bootstrap_packages`: Array of strings, mandatory: The `glibc` and
   `nss-altfiles` packages (and ideally nothing else) must be in this
   set; rpm-ostree will modify the `/etc/nsswitch.conf` in the target
   root to ensure that `/usr/lib/passwd` is used.

 * `packages`: Array of strings, mandatory: Set of installed packages.
   Names prefixed with an `@` (e.g. `@core`) are taken to be the names
   of comps groups.

 * `units`: Array of strings, optional: Systemd units to enable by default

 * `default_target`: String, optional: Set the default systemd target

 * `include`: string, optional: Path to another treefile which will be
   used as an inheritance base.  The semantics for inheritance are:
   Non-array values in child values override parent values.  Array
   values are concatenated.  Filenames will be resolved relative to
   the including treefile.
