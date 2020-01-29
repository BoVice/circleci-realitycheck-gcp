# realitycheck-gcp

## Summary
A sample app that validates some basic CircleCI features in two parallel workflows.

**NOTE**: Please read the entirety of this README before continuing. There are some important prerequisites.

To run realitycheck, fork the repository and start building it on your installation of CircleCI.

Descriptions of the two workflows follow.

## `resource_class` workflow

Tests all known `resource_class` options—queries the CircleCI API to verify that jobs ran with the requested resources.

### Prerequisites
- Your Nomad client instances must be large enough to accommodate these resource classes — see our [Configuration Reference](https://circleci.com/docs/2.0/configuration-reference/#resource_class) for details on the available resource classes and [our server docs](https://circleci.com/docs/2.0/nomad/#auto-scaling-policy-best-practices) about sizing your Nomad client instances.
- The base URL of your CircleCI installation (e.g. https://circleci.com) must be specified via a `CIRCLE_HOSTNAME` project environment variable
- A personal API token (see `CIRCLE_HOSTNAME/account/api` URL endpoint) must be stored as a `CIRCLE_TOKEN` project environment variable


## Features workflow
- Tests ability to save and restore [caches](circleci.com/docs/2.0/caching)
- Tests writing to and reading from [workspaces](https://circleci.com/docs/2.0/workflows/#using-workspaces-to-share-data-among-jobs)
- Tests the default `org-global` [context](https://circleci.com/docs/2.0/contexts) (*NOTE:* needs a key called `CONTEXT_END_TO_END_TEST_VAR` to exist in a context called `org-global`) 
- Tests multiple contexts (*NOTE:* needs a key called `MULTI_CONTEXT_END_TO_END_VAR` to exist in a context called `individual-local`)
- Tests upload/storage of [artifacts](https://circleci.com/docs/2.0/artifacts) and [test results](https://circleci.com/docs/2.0/collect-test-data)

### Prerequisites
You will need to configure the following contexts and keys (their values can be anything). Docs on how to set up contexts [can be found here](https://circleci.com/docs/2.0/contexts/).

Context Name     | Key Name                       
-----------------|-----------------------------
org-global       | CONTEXT_END_TO_END_TEST_VAR
individual-local | MULTI_CONTEXT_END_TO_END_VAR
