# Contributing to vscode-r

## Install

1. install npm and Node.js
1. install Visual Studio Code

```sh
git clone https://github.com/Ikuyadeu/vscode-R.git
cd vscode-R
npm install # install required packages for vscode-R
code . # run VS Code
```

## Test

* In VS Code: 'File' -> 'Open Folder...' and select 'vscode-R' (the directory with your edits)
* Press `F5`
* A new VS Code window should open, with '[Extension Development Host]' in the title bar. This is running your modified version of vscode-R

## Lint
We use [eslint](https://eslint.org/) for linting our sources. You can run eslint across the sources by calling yarn eslint from a terminal or command prompt. 

To lint the source as you make changes you can install the [eslint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint).

## Pull Request

* Fork it(via GitHub) in your account
* Add your project URL

```sh
git remote add mine https://github.com/yourname/vscode-R.git
```

* Create your feature branch

```sh
git checkout -b my-new-feature
```

* Commit your changes

```sh
git commit -am 'Add some feature'
```

* Push to the branch

```sh
git push mine my-new-feature
```

* Create new Pull Request(via GitHub)