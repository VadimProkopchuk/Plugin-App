# Plugin-App

.NET Core app with plugins

## Create solution

```
mkdir Plugin-App
cd .\Plugin-App\

dotnet new sln
dotnet new console -o AppWithPlugin
dotnet new classlib -o PluginBase
dotnet new classlib -o HelloPlugin
dotnet new classlib -o JsonPlugin

Remove-Item -Path PluginBase/Class1.cs
Remove-Item -Path HelloPlugin/Class1.cs
Remove-Item -Path JsonPlugin/Class1.cs

New-Item -Path PluginBase/ICommand.cs
New-Item -Path AppWithPlugin/PluginLoadContext.cs
New-Item -Path HelloPlugin/HelloCommand.cs
New-Item -Path JsonPlugin/JsonCommand.cs

dotnet sln add AppWithPlugin/AppWithPlugin.csproj
dotnet sln add PluginBase/PluginBase.csproj
dotnet sln add HelloPlugin/HelloPlugin.csproj
dotnet sln add JsonPlugin/JsonPlugin.csproj

dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj
dotnet add JsonPlugin/JsonPlugin.csproj package Newtonsoft.Json
```

## Build

```
donet build
```

## Run

```
cd .\AppWithPlugin\
dotnet run
```
