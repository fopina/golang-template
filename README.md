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
* [ ] Add [codecov](https://app.codecov.io/github/fopina/) token
    * `CODECOV_TOKEN` taken from link above; OR
* [ ] Replace this README.md - template below

## Notes

### Feature branch publishing

`publish-dev` workflow tests and publishes branches:
* Binaries are uploaded as artifacts to the run
* Docker image is tagged as `dev-BRANCH` and pushed to GCHR as well

## ---


<img src="https://github.com/fopina/golang-template/actions/workflows/test.yml/badge.svg" alt="drawing"/>
<img src="https://github.com/fopina/golang-template/actions/workflows/lint.yml/badge.svg" alt="drawing"/>
<img src="https://pkg.go.dev/badge/github.com/fopina/golang-template.svg" alt="drawing"/>
<img src="https://codecov.io/gh/FalcoSuessgott/golang-cli-template/branch/main/graph/badge.svg" alt="drawing"/>
<img src="https://img.shields.io/github/v/release/FalcoSuessgott/golang-cli-template" alt="drawing"/>
<img src="https://img.shields.io/docker/pulls/falcosuessgott/golang-cli-template" alt="drawing"/>
<img src="https://img.shields.io/github/downloads/FalcoSuessgott/golang-cli-template/total.svg" alt="drawing"/>
</div>


# Demo Application

```sh
$> golang-template -h
golang-cli project template demo application

Usage:
  golang-template [flags]
  golang-template [command]

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
