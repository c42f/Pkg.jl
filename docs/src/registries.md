# **7.** Registries

Registries contain information about packages, such as
available releases, dependencies and where it can be downloaded.
The `General` registry (https://github.com/JuliaRegistries/General)
is the default one, and is installed automatically.

## **7.1.** Managing registries

Registries can be added, removed and updated from either the Pkg REPL
or by using the functional API. In this section we will describe the
REPL interface. The functional registry API is documented in
the [Registry API Reference](@ref) section.

### Adding registries

A custom registry can be added with the `registry add` command
from the Pkg REPL. Usually this will be done with a URL to the
registry. Here we add the `General` registry

```
pkg> registry add https://github.com/JuliaRegistries/General
   Cloning registry from "https://github.com/JuliaRegistries/General"
     Added registry `General` to `~/.julia/registries/General/SxLXF`
```

and now all the packages registered in `General` are available for e.g. adding.
To see which registries are currently installed you can use the `registry status`
(or `registry st`) command

```
pkg> registry st
Registry Status
 [23338594] General (https://github.com/JuliaRegistries/General.git)
```

Registries are always added to the user depot, which is the first entry in `DEPOT_PATH`.

### Removing registries

Registries can be removed with the `registry remove` (or `registry rm`) command.
Here we remove the `General` registry

```
pkg> registry rm General
  Removing registry `General` from ~/.julia/registries/General/SxLXF

pkg> registry st
Registry Status
 (no registries found)
```

In case there are multiple registries named `General` installed you have to
disambiguate with the `uuid`, just as when manipulating packages, e.g.

```
pkg> registry rm General=23338594-aafe-5451-b93e-139f81909106
  Removing registry `General` from ~/.julia/registries/General/SxLXF
```

### Updating registries

The `registry update` (or `registry up`) command is available to update registries.
Here we update the `General` registry,

```
pkg> registry up General
```

and to update all installed registries just do

```
pkg> registry up
```


## **7.2.** Creating a registry

TBW: Describe registry file structure etc.
