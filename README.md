# MSB5029-ArtifactsOutput-Bug
Reproduction of bug in .NET SDK 9

## Reproduction Steps

`dotnet restore ConsoleApp` yields:
```
MSBUILD : warning MSB5029: The value "/**" of the "Exclude" attribute in element <ItemGroup> in file "C:\Program Files\dotnet\sdk\9.0.101\Sdks\Microsoft.NET.Sdk\targets\Microsoft.NET.Sdk.DefaultItems.props (36,62)" is a wildcard that results in enumerating all files on the drive, which was likely not intended. Check that referenced properties are always defined and that the project and current working directory are not at the drive root.
    C:\Program Files\dotnet\sdk\9.0.101\Sdks\Microsoft.NET.Sdk\targets\Microsoft.NET.Sdk.DefaultItems.props(36,62): error MSB5029: The value "/**" of the "Exclude" attribute in element <ItemGroup> in file "C:\Program Files\dotnet\sdk\9.0.101\Sdks\Microsoft.NET.Sdk\targets\Microsoft.NET.Sdk.DefaultItems.props (36,62)" is a wildcard that results in enumerating all files on the drive, which was likely not intended. Check that referenced properties are always defined and that the project and current working directory are not at the drive root.

Restore failed with 1 error(s) and 1 warning(s) in 0.1s
```
Changing the used dotnet sdk to 8.0.X and `dotnet restore ConsoleApp` succeeds.