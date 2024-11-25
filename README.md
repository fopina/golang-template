# golang template

Template based off another template: github.com/fopina/golang-template

> README has not been updated!

## Content

* `goreleaser` setup with both binary and docker
* `.github` with actions ready to be used
    * [test](.github/workflows/test.yml) runs unit tests
    * [goreleaser](.github/workflows/goreleaser.yml) publishes semver tags to:
      * binaries to github releases
      * docker image to ghcr.io

## New project checklist

* [ ] Replace every .go file with the actual code :D
* [ ] Replace `github.com/fopina/golang-template` globally with new package name
    * At least `main.go` and `go.mod` should be left after previous step
* [ ] Replace `LICENSE` if MIT does not apply
* [ ] Search the project for `# TODO` to find the (minimum list of) places that need to be changed.
* [ ] Add [codecov](https://app.codecov.io/github/fopina/) token or allow tokenless uploads
    * `CODECOV_TOKEN` taken from link above; OR
    * https://app.codecov.io/account/github/fopina/org-upload-token for allowing tokenless
* [ ] Replace this README.md - template below

## Notes

### Feature branch publishing

`publish-dev` workflow publishes `dev`/`dev-*` branches to [testpypi](https://test.pypi.org).

Other common approach to publish dev branches is to use pre-release channels: version the package with a `rc` or `beta` suffix (such as `1.0.0-beta1`) and pypi will consider pre-release. In order to install this, the user needs to do `pip install PACKAGE --pre` otherwise the latest stable is picked up.  
However this will "pollute" your pypi index and it still requires you to bump the version (`1.0.0-beta1` < `1.0.0`) or to install the branch using specific version.

Yet another approach is to simply use an entirely different package name for the dev releases. Tensorflow does that, for example, with [tf-nightly](https://pypi.org/project/tf-nightly/).

## ---

<div align="center">
A general purpose project template for golang CLI applications
<br>
<br>
This template serves as a starting point for golang commandline applications it is based on golang projects that I consider high quality and various other useful blog posts that helped me understanding golang better.
<br>
<br>
<img src="https://github.com/fopina/golang-template/actions/workflows/test.yml/badge.svg" alt="drawing"/>
<img src="https://github.com/fopina/golang-template/actions/workflows/lint.yml/badge.svg" alt="drawing"/>
<img src="https://pkg.go.dev/badge/github.com/fopina/golang-template.svg" alt="drawing"/>
<img src="https://codecov.io/gh/FalcoSuessgott/golang-cli-template/branch/main/graph/badge.svg" alt="drawing"/>
<img src="https://img.shields.io/github/v/release/FalcoSuessgott/golang-cli-template" alt="drawing"/>
<img src="https://img.shields.io/docker/pulls/falcosuessgott/golang-cli-template" alt="drawing"/>
<img src="https://img.shields.io/github/downloads/FalcoSuessgott/golang-cli-template/total.svg" alt="drawing"/>
</div>

# Table of Contents
<!--ts-->
   * [golang-cli-template](#golang-cli-template)
   * [Features](#features)
   * [Project Layout](#project-layout)
   * [How to use this template](#how-to-use-this-template)
   * [Demo Application](#demo-application)
   * [Makefile Targets](#makefile-targets)
   * [Contribute](#contribute)

<!-- Added by: morelly_t1, at: Tue 10 Aug 2021 08:54:24 AM CEST -->

<!--te-->

# Features
- [goreleaser](https://goreleaser.com/) with `deb.` and `.rpm` packer and container (`docker.hub` and `ghcr.io`) releasing including `manpages` and `shell completions` and grouped Changelog generation.
- [golangci-lint](https://golangci-lint.run/) for linting and formatting
- [Github Actions](.github/worflows) Stages (Lint, Test (`windows`, `linux`, `mac-os`), Build, Release) 
- [Gitlab CI](.gitlab-ci.yml) Configuration (Lint, Test, Build, Release)
- [cobra](https://cobra.dev/) example setup including tests
- [Makefile](Makefile) - with various useful targets and documentation (see Makefile Targets)
- [Github Pages](_config.yml) using [jekyll-theme-minimal](https://github.com/pages-themes/minimal) (checkout [https://falcosuessgott.github.io/golang-cli-template/](https://falcosuessgott.github.io/golang-cli-template/))
- Useful `README.md` badges
- [pre-commit-hooks](https://pre-commit.com/) for formatting and validating code before committing

# Project Layout
* [assets/](https://pkg.go.dev/github.com/fopina/golang-template/assets) => docs, images, etc
* [cmd/](https://pkg.go.dev/github.com/fopina/golang-template/cmd)  => commandline configurartions (flags, subcommands)
* [pkg/](https://pkg.go.dev/github.com/fopina/golang-template/pkg)  => packages that are okay to import for other projects
* [internal/](https://pkg.go.dev/github.com/fopina/golang-template/pkg)  => packages that are only for project internal purposes
- [`tools/`](tools/) => for automatically shipping all required dependencies when running `go get` (or `make bootstrap`) such as `golang-ci-lint` (see: https://github.com/golang/go/wiki/Modules#how-can-i-track-tool-dependencies-for-a-module)
)
- [`scripts/`](scripts/) => build scripts 

# How to use this template
```sh
bash <(curl -s https://raw.githubusercontent.com/FalcoSuessgott/golang-cli-template/master/install.sh)
```

In order to make the CI work you will need to have the following Secrets in your repository defined:

Repository  -> Settings -> Secrets & variables -> `CODECOV_TOKEN`, `DOCKERHUB_TOKEN` & `DOCKERHUB_USERNAME`

# Demo Application

```sh
$> golang-cli-template -h
golang-cli project template demo application

Usage:
  golang-cli-template [flags]
  golang-cli-template [command]

Available Commands:
  completion  Generate the autocompletion script for the specified shell
  example     example subcommand which adds or multiplies two given integers
  help        Help about any command
  version     golang-cli-template version

Flags:
  -h, --help   help for golang-cli-template

Use "golang-cli-template [command] --help" for more information about a command.
```

```sh
$> golang-cli-template example 2 5 --add
7

$> golang-cli-template example 2 5 --multiply
10
```

# Makefile Targets
```sh
$> make
bootstrap                      install build deps
build                          build golang binary
clean                          clean up environment
cover                          display test coverage
docker-build                   dockerize golang application
fmt                            format go files
help                           list makefile targets
install                        install golang binary
lint                           lint go files
pre-commit                     run pre-commit hooks
run                            run the app
test                           display test coverage
```

# Contribute
If you find issues in that setup or have some nice features / improvements, I would welcome an issue or a PR :)
