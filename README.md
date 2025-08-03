# DotNetTestResults
[![CI/CD](https://github.com/samsmithnz/DotNetTestResults/actions/workflows/workflow.yml/badge.svg)](https://github.com/samsmithnz/DotNetTestResults/actions/workflows/workflow.yml)

Displays .NET test results to the actions summary.

To use, we need two steps in our GitHub Actions workflow:
1. Update the `dotnet test` step to output a trx formatted file, adding `-l:"trx;LogFileName=${{ github.workspace }}/TestOutput.xml"`

For example:
```
    - name: .NET test
      run: dotnet test src/MyProject.Tests/MyProject.Tests.csproj -l:"trx;LogFileName=${{ github.workspace }}/TestOutput.xml"

```

2. Pass in the trx file path from the test step to this action:

```
    - uses: samsmithnz/DotNetTestResults@0.1.0
      with:
        fileName: ${{ github.workspace }}/TestOutput.xml
```

The result displays in the summary like this: 

<img width="3239" height="1725" alt="image" src="https://github.com/user-attachments/assets/40562aad-6032-47d7-afa5-0b4ec1fce2c3" />
