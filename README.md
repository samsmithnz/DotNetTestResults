# DotNetTestResults
[![CI/CD](https://github.com/samsmithnz/DotNetTestResults/actions/workflows/workflow.yml/badge.svg)](https://github.com/samsmithnz/DotNetTestResults/actions/workflows/workflow.yml)

To use, we need two steps
1. Update the dotnet test step to output a trx formatted file, adding `-l:"trx;LogFileName=${{ github.workspace }}/TestOutput.xml"`

For example:
```
    - name: .NET test
      run: dotnet test src/MyProject.Tests/MyProject.Tests.csproj -l:"trx;LogFileName=${{ github.workspace }}/TestOutput.xml"

```

2. pass in the trx file location from the test step

```
    - uses: samsmithnz/DotNetTestResults@main
      with:
        fileName: ${{ github.workspace }}/TestOutput.xml
```