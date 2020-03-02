Mainly for RStudio user to find similar editor features in VSCode

## C/C++

[C/C++](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) to write Rcpp

`.vscode/c_cpp_properties.json`:

```json
{
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "${workspaceFolder}/**",
                "${env:HOME}/R/x86_64-pc-linux-gnu-library/3.6/Rcpp/include",
                "/usr/share/R/include"
            ],
            "defines": [],
            "compilerPath": "/usr/bin/gcc",
            "cStandard": "c11",
            "cppStandard": "c++17",
            "intelliSenseMode": "clang-x64"
        }
    ],
    "version": 4
}
```

`.clang-format`:

```
---
Language: Cpp
BasedOnStyle: LLVM
Standard: Cpp11
ReflowComments: false
---
```

Settings:

```json
"C_Cpp.commentContinuationPatterns": [
    "/**",
    "//'"
]
```

## Path Autocomplete

[Path Autocomplete](https://marketplace.visualstudio.com/items?itemName=ionutvmi.path-autocomplete)

```json
"path-autocomplete.pathMappings": {
    "/": "/",
    "./": "${folder}"
}
```