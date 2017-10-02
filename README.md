Reproduce of msbuild bug
========================

First reported at

https://stackoverflow.com/questions/46526428/msbuild-solutiondir-resolves-incorrectly-to-c-when-running-msbuild-tresto

Reproduction steps
==================

From the command line just do

    dotnet restore

The error you should see is

    C:\Users\phelan\workspace\MSBUILDBUG\Test\Test.csproj(8,3): error MSB4019: The imported project "C:\Solution.props" was not found. Confirm that the path in the <Import> declaration is correct, and that the file exists on disk.
    C:\Users\phelan\workspace\MSBUILDBUG\Test\Test.csproj : warning NU1503: Skipping restore for project 'C:\Users\phelan\workspace\MSBUILDBUG\Test\Test.csproj'. The project file may be invalid or missing targets required for restore. [C:\Users\phelan\workspace\MSBUILDBUG\MSBUILDBUG.sln]
    C:\Program Files\dotnet\sdk\2.0.0\NuGet.targets(102,5): warning : Unable to find a project to restore! [C:\Users\phelan\workspace\MSBUILDBUG\MSBUILDBUG.sln]

however if you do

   dotnet msbuild

works fine with no error on the SolutionDir variable
