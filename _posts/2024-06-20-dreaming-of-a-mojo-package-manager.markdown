---
layout: post
title:  "Dreaming of a mojo package manager"
date:   2024-06-20 11:48:17 -0600
---

I began learning [Mojo](https://www.modular.com/max/mojo) and noticed there wasn't a native default package manager and i began dreaming one up after doing a bit of research:

What currently exists:

* [PKM - Mojo's unofficial community package manager](https://github.com/Hammad-hab/pkm)
* [Mod - Mojo Dependency Manager](https://github.com/better-mojo/mod)
* [Poor persons package management in Mojo](https://mzaks.medium.com/poor-persons-package-management-in-mojo-8671aa6e420a)

What the community is discussing and requesting:

* [What is mojo's package manager](https://github.com/modularml/mojo/discussions/1171)
* [Mojo Project Manifest Discussion](https://github.com/modularml/mojo/discussions/1785)
* [Mojo Projet Manifest Proposal](https://github.com/modularml/mojo/blob/main/proposals/project-manifest-and-build-tool.md)
* [Auto patch 3rd party imports to mitigate dependency hell](https://github.com/modularml/mojo/discussions/1401) 
* [Rust import the same create different versions](https://stackoverflow.com/questions/58739075/how-do-i-import-multiple-versions-of-the-same-crate)
* [For the Mojo package manager, consider making prebuilt binaries work from the start](https://github.com/modularml/mojo/discussions/2772)

I would use the name Mojic and use a Mojic.toml and Mojic.lock similar to how Rust's cargo does it.  

```toml
[dependencies]
futures_01 = { package = "futures", version = "0.1.0", type = "src", repo = "https://github.com/rust-lang/futures-rs" }
futures_03 = { package = "futures", version = "0.3.0" }
```

I would also add in a type of wether to use src or mojopkg, defaults to mojopkg.

If we soley use mojopkg could the compiler deduplicate dependencies of the same version across dependent mojopkg's?  Either way we will still need compiling from source from local paths or git repos so it won't matter.

Then comes mojic.org a mojopkg repository with: User auth, package publishing api, reference to the package's git repo, etc.

Anyways it's a fun dream. :) 

