# tfsecurity-action
Run tfsecurity as a GitHub action with configurable output

To add the action, add `tfsecurity.yml` into the `.github/workflows` directory in the root of your Github project.

The contents of `tfsecurity.yml` should be;

```yaml
name: tfsecurity
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  tfsecurity:
    name: tfsecurity
    runs-on: ubuntu-latest

    steps:
      - name: Clone repo
        uses: actions/checkout@master
      - name: tfsecurity
        uses: khulnasoft-labs/tfsecurity-action@v1.0.0
```

Run tfsecurity as part of a GitHub Action flow. Optionally prevent the failure of tfsecurity from breaking the build or pass additional arguments using `additional_args`.

## Optional inputs

There are a number of optional inputs that can be used in the `with:` block.

**working_directory** - the directory to scan in, defaults to `.`, ie current working directory

**version** - the version of tfsecurity to use, defaults to `latest`

**format** - Default format can be overridden to any of the following - [json,csv,checkstyle,junit,sarif]

**additional_args** - any additional arguments you want to have passed to tfsecurity

**soft_fail** - set to `true` if you dont want the action to break the build

**github_token** - a GitHub token to be used when calling the GitHub API, which helps in avoiding rate-limiting

### tfsecurity_vars

`tfsecurity` provides an [extensive number of arguments](https://khulnasoft-labs.github.io/tfsecurity/v1.0.1/getting-started/usage/) which can be passed through as in the example below;

```yaml
name: tfsecurity
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  tfsecurity:
    name: tfsecurity
    runs-on: ubuntu-latest

    steps:
      - name: Clone repo
        uses: actions/checkout@master
      - name: tfsecurity
        uses: khulnasoft-labs/tfsecurity-action@v1.0.0
        with:
          soft_fail: true

```

## Open Source Attribution

- bash: [GPL 3.0 or later](https://www.gnu.org/licenses/gpl-3.0.html)
- curl: [curl license](https://curl.se/docs/copyright.html)
- git: [GPL 2.0 or later](https://github.com/git/git/blob/master/COPYING)
- jq: [MIT](https://github.com/stedolan/jq/blob/master/COPYING) 

## License

[MIT License](https://github.com/khulnasoft-labs/tfsecurity-action/blob/master/LICENSE)
