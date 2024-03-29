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

## codespaces

- created codespace
  - add config
  - add dotenv

## feedback

- in the guide, should explain what the cli commands are doing
  - it's bad practice from a security standpoint to just copy and paste commands without understanding what they do, we should encourage best behavior in all aspects
- tf install mac os; 1.7.5 is current arm version, listed version is outdated, released june 2 2021, should cause no issues with the M chips following the steps in the guide
  - brew upgrade tf step is redundant if you move `brew update` to the step before *tapping* the hashicorp repo, makes the workflow more efficient
- aws ui has changed significantly since the guide was written, the guide should be updated to reflect the current state of the aws console
