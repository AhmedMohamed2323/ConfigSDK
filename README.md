# ConfigSDK
The config SDK, dynamic config, and config polices can be used to create a centralized config management system.

Prerequisites

A project with a CircleCI config.yml
A CircleCI scale plan (only needed for config policies)

Advantages

Locks down who can manipulate CircleCI configs
Allows for automated distribution of config updates
Can use CircleCI to test and deploy config changes
Creating the centralized config repository.

Create a repository for your config SDK module(s). Install the config SDK and create a Javascript/Typescript module.

The module can be as dynamic as you’d like, generating configs for multiple environments and/or projects. To start, it may be beneficial to translate current config files into individual JS/TS modules to take advantage of centralized configuration sooner.

Once you are happy with the module, publish the package via NPM.