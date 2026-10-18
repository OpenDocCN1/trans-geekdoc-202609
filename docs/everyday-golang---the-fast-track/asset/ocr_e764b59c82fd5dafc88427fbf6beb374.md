In our example, we’ll first checkout the code from GitHub for the release tag, then run make all, followed by uploading the release artifacts to the GitHub release.

```
name: publish
on:
  push:
    tags:
      - '*'
jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
        with:
          fetch-depth: 1
      - name: Make all
        run: make all
      - name: Upload release binaries
        uses: alexellis/upload-assets@0.4.1
        env:
          GITHUB_TOKEN: ${{ github.token }}
        with:
          asset_paths: '["./bin/release-it*"]'
```

Each step in the workflow file can use a specific GitHub Action like alexellis/upload-assets@0.4.1 or actions/checkout@master, but when you leave that field blank, it uses the base system such as ubuntu-latest. On the base Ubuntu runner you can execute standard shell and build commands like make all.

The alexellis/upload-assets action is one that I built to use on all the various OSS projects I maintain and allows a number of files to be uploaded.

Users can then go ahead and download your binary and run it on their system.

For instance:

```
$ cd /tmp/
$ curl -sLSf \
  -o ./release-it \
  https://github.com/alexellis/release-it/releases/download/0.2.11/release-it-darwin \
  && chmod +x ./release-it \
  && ./release-it

release-it: 0.2.11, commit: 4379cbf694c55bd98f5080d76ac5972fd89dcc65
```