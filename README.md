## GitHub Action to Create Releases Based on a Keyword
The Keyword Releaser will create a release based on the keyword specified in the argument.
<br>

## Environment Variables
* `GITHUB_TOKEN` - Required Allows the Action to authenticate with the GitHub API to create the release.
<br>

### Arguments
* Required - A single keyword. If the keyword is found in a commit message, a release will be created. Although case is ignored, it's suggested to use a unique, uppercase string like `FIXED`, `READY_TO_RELEASE`, or maybe even `PINEAPPLE`.
<br>

## Examples

Here's an example workflow that uses the Keyword Releaser action. The workflow is triggered by a `PUSH` event and looks for the keyword `"FIXED"`.

<pre>
name: keyword-releaser

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - uses: lemar5555/release-action@master
      env:
        GITHUB_TOKEN ${{ secrets.GITHUB_TOKEN }}
      with:
        args: 'FIXED'
</pre>