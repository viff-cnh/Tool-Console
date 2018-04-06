# Tool-Console for VIFF

This branch of Tool Console contains the Landis model configuration used in the Visualizing Forest Futures (VIFF) project.

## Prerequisites
- [.NET Core 2.0](https://www.microsoft.com/net/download)
- [GDAL](http://www.gdal.org/) (not required for Windows 10, Ubuntu, and possibly other recent Linux distributions; see documentation [here](https://github.com/viff-cnh/docs/blob/master/gdal_build_notes.md).)

## Running a Landis scenario

Clone the repository

```Shell
git clone https://github.com/viff-cnh/Tool-Console.git
```

Navigate to the root of the cloned repository and build the Tool-Console project:

```Shell
cd src
dotnet build -c Release #set to 'Debug' for debug builds
```

Within the root of the cloned repository, the built Tool-Console executable DLL will be located at:

```Shell
src/bin/Release/netcoreapp2.0/Landis.Console.dll # change `Release` to 'Debug' for debug builds
```

Under .NET Core, the executable is run with the dotnet command:

```Shell
dotnet Landis.Console.dll
```

On Windows 10, Ubuntu, and possibly other recent Linux distribution, the executable can be used out-of-the-box to run different VIFF scenarios (available on [Box](https://psu.box.com/s/u0fhzwf4b663tqxyafhohg3yu6h3g0jx)). On other platforms, [additional steps for GDAL](https://github.com/viff-cnh/docs/blob/master/gdal_build_notes.md) are required before running a scenario.

## Update Procedures

The software development workflow for the VIFF Tool-Console is different than the standard Landis workflow. Because VIFF Tool-Console uses .NET Core, all required Landis libraries and extensions are specified as Nuget package dependencies in the Tool-Console [project file](https://github.com/viff-cnh/Tool-Console/blob/dotnetore-20-viff-scen/src/Console.csproj). So that VIFF Tool-Console can load all required extensions, we include the [extensions.xml](https://github.com/viff-cnh/Tool-Console/blob/dotnetore-20-viff-scen/src/extensions.xml) along with the project.

If a new extension is required, the update procedures is as follows:

- Update the [project file](https://github.com/viff-cnh/Tool-Console/blob/dotnetore-20-viff-scen/src/Console.csproj) to include a dependency on the extension's Nuget package
- Add an entry to  [extensions.xml](https://github.com/viff-cnh/Tool-Console/blob/dotnetore-20-viff-scen/src/extensions.xml) for the extension. Extension entries are specified with the [Extension Admin Tool](https://github.com/viff-cnh/Tool-Extension-Admin).   

## Notes

Changes to this repository are governed by the [**Repository Rules**](https://sites.google.com/site/landismodel/developers) from the Technical Advisory Committee.

Robert Scheller is the custodian of this repository.

For older commits, see: https://github.com/LANDIS-II-Foundation/Core-Model/tree/master/model/console-archive
