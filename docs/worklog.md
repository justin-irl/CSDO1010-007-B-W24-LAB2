# record of work

## aws setup

- already had a recently created free tier account
- updated according to doc
  - admin user created
    - admin permissions granted via permission set
    - access key and secret key generated
      - revisit to auto rotating keys
    - mfa set for root and admin accounts

## terraform setup

- tapped hashicorp repo
  - tf installed, version 1.7.5

## Vscode setup

- already installed
  - extension added

## repo + local env setup

- repo created
  - tfenv configured
  - strict versioning set
  - `../main.tf` updated to current tf version
    - `1.7.5`

error on `terraform init`:

```sh
$ ❯ terraform init

Initializing the backend...
Initializing modules...

Initializing provider plugins...
- Finding hashicorp/aws versions matching "~> 3.44.0"...
- Finding latest version of hashicorp/template...
- Installing hashicorp/aws v3.44.0...
- Installed hashicorp/aws v3.44.0 (signed by HashiCorp)
╷
│ Error: Incompatible provider version
│
│ Provider registry.terraform.io/hashicorp/template v2.2.0 does not have a package available for your current platform, darwin_arm64.
│
│ Provider releases are separate from Terraform CLI releases, so not all providers are available for all platforms. Other versions of
│ this provider may have different platforms supported.
```

## fix

```sh
#control versioning by project:
brew install tfenv

# add `terraform-version`:
tfenv pin
```

```sh
\$ ❯ brew install kreuzwerker/taps/m1-terraform-provider-helper
```

run

```sh
$ ❯ m1-terraform-provider-helper activate

/usr/local/bin
$ ❯ m1-terraform-provider-helper install hashicorp/template -v v2.2.0
```

reload shell

then

```sh
terraform init && terraform validate && terraform ftm
```

update `./main/tf` to include:

```tf
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "5.43.0"
    }
  }
}
```

<!-- ## codespaces

- created codespace
  - add config
  - add dotenv -->

## feedback

- in the guide, should explain what the cli commands are doing
  - it's bad practice from a security standpoint to just copy and paste commands without understanding what they do, we should encourage best behavior in all aspects
- tf install mac os; 1.7.5 is current arm version, listed version is outdated, released june 2 2021, should cause no issues with the M chips following the steps in the guide
  - brew upgrade tf step is redundant if you move `brew update` to the step before *tapping* the hashicorp repo, makes the workflow more efficient
- aws ui has changed significantly since the guide was written, the guide should be updated to reflect the current state of the aws console
