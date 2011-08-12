# Base Directory Standards

The purpose of this project is to take the [XDG Base Directory Standard](http://standards.freedesktop.org/basedir-spec/latest/)
and [XDG User Directory Standard](http://www.freedesktop.org/wiki/Software/xdg-user-dirs) (collectively *XDG*),
as a starting point for a universal standard suitable for inclusion in the FHS.

## CONSIDERATIONS

### Fixed HOME Directories

Rather than configurable home directories BDS defines fixed locations.
The configuration file store is *always* `~/.config`, the temporary
file store is *always* ~/.cache` and local "usr" store is alwasy `~/.local`.
These directories can still be "reconfigured", but via symlinks rather
then environment variables.

### Generalized .local

The `~/.local` directory that is part of the `$XDG_DATA_HOME`
default path is an explicit part of the BDS standard.
(In the Ruby XDG library this has been labeled `$XDG_RESOURCE_HOME`.)
This directory is simply the per-user equivalent of the system wide
`/usr/local` directory.

### CONFIG Directories Default

For a universal standard, the current default path in `$XDG_CONFIG_DIRS`
should change from `/etc/xdg` to `/etc`.

### Removal of XDG Prefix

The `XDG` prefix is removed from the environment variables. The variable 
become:

    $CONFIG_DIRS  /etc/
    $DATA_DIRS    /usr/local/share/:/usr/share/
    $CACHE_DIRS   /tmp/

### Equivalent for /var.

XDG lacks a corresponding directory for `/var`, although the latest version
provides `$XDG_RUNTIME_DIR` which corresponds to `/var/run`.

In BDS this is supported as the fixed location `~/.variable`, where 
`~/.variable/run` follows all the rules layed about by the XDG standard for
`$XDG_RUNTIME_DIR`.

