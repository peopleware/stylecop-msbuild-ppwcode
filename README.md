# StyleCop.MSBuild.PPWCode

This NuGet package provides [StyleCop] MSBuild integration with the PPWCode 
style conventions.


## Getting started

The package is available from the [NuGet] central package repository: the
[NuGet Gallery].

The package can be installed on a project by project basis by using the
NuGet package manager from inside Visual Studio.

During package installation, a hook will be placed in the project build
which will trigger StyleCop.  From then on, the build output will also
contain StyleCop warnings.

StyleCop warnings can be spotted easily in the build output because these
warnings always start with a prefix of the form `SAxxxx`, with `xxxx` a
number referring to the specific StyleCop rule that was violated.

Note that there is no need to install StyleCop when using this NuGet package.
The NuGet package includes a version of StyleCop which is used transparently.


## Style settings

Note that complete documentation is available at [StyleCop documentation].

The package contains a StyleCop settings configuration that reflects the code
style that is followed throughout all the PPWCode projects.

Even if this style is no match with the coding style you wish to follow in
your own projects, this package can still be usefull. It is possible to
override the included settings in the following ways.

### Use own StyleCop settings files

It is possible to completely override the included settings by using another
settings file on a project by project basis.  The preferred setttings file must
be placed in the root of the project.

For more information, see [StyleCop settings across projects].

### Locally disable specific rules

The StyleCop settings that are configured for PPWCode are pretty strict. Sometimes
it is desirable to disable specific rules locally, without disabling the rules
alltogether over the whole of the project.

Disabling specific rules can be done using a specific `SuppressMessage` attribute.
We illustrate this with a couple of examples. For more complete documentation,
please consult the StyleCop documentation: [StyleCop Rule Suppressions].

#### Example: disable specific rule

The following example shows how to disable a specific rule.

    [SuppressMessage(
        "StyleCop.CSharp.NamingRules",
        "SA1302:InterfaceNamesMustBeginWithI",
        Justification = "Reviewed. Suppression is OK here.")] 
    public interface MyInterface
    { 
        int GiveMeAnInt();
    }

Note that it is required to add a `justification` when suppressing a rule.


#### Example: disable class of rules

The following example shows how to disable all naming rules.

    [SuppressMessage(
        "StyleCop.CSharp.NamingRules",
        "*",
        Justification = "Reviewed. Suppression is OK here.")] 
    public interface MyInterface
    { 
        int GiveMeAnInt();
    }

Note that also in this case a `justification` must be added.
    

## Contributors

See the [GitHub Contributors list].


## PPWCode

This package is part of the PPWCode project, developed by [PeopleWare n.v.].

More information can be found in the following locations:
* [PPWCode project website]
* [PPWCode Google Code website]

Please note that not all information on those sites is up-to-date. We are
currently in the process of moving the code away from the Google code
subversion repositories to git repositories on [GitHub].


### PPWCode .NET

Specifically for the .NET libraries: new development will be done on the
[PeopleWare GitHub repositories], and all new stable releases will also
be published as packages on the [NuGet Gallery].

We believe in Design By Contract and have good experience with
[Microsoft Code Contracts] and the related tooling.  As such, our packages
always include Contract Reference assemblies.  This allows you to also
benefit as a user from the contracts that are already included in the
library code.

The packages also include both the pdb and xml files, for debugging symbols
and documentation respectively.  In the future we might look into using
symbol servers.


## License and Copyright

Copyright 2014 by [PeopleWare n.v.].

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.


### StyleCop

A release of StyleCop is embedded in this package.

StyleCop is licensed under the Microsoft Public License (see [StyleCop License]).



[PPWCode project website]: http://www.ppwcode.org
[PPWCode Google Code website]: http://ppwcode.googlecode.com

[PeopleWare n.v.]: http://www.peopleware.be/

[NuGet]: https://www.nuget.org/
[NuGet Gallery]: https://www.nuget.org/policies/About

[GitHub]: https://github.com
[PeopleWare GitHub repositories]: https://github.com/peopleware

[Microsoft Code Contracts]: http://research.microsoft.com/en-us/projects/contracts/

[StyleCop]: http://stylecop.codeplex.com/
[StyleCop License]: http://stylecop.codeplex.com/license
[StyleCop documentation]: https://stylecop.codeplex.com/documentation
[StyleCop settings across projects]: https://stylecop.codeplex.com/wikipage?title=Sharing%20StyleCop%20Settings%20Across%20Projects&referringTitle=Documentation
[StyleCop Rule Suppressions]: https://stylecop.codeplex.com/wikipage?title=Rule%20Suppressions&referringTitle=Documentation

[GitHub Contributors list]: https://github.com/peopleware/stylecop-msbuild-ppwcode/graphs/contributors
