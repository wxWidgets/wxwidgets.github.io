---
title: "GitHub Action for Projects Using MSVC"
date: 2026-11-12
comments: true
tags: ci, msvc, github
---

There is a new GitHub action for [setting up wxWidgets][setup-wx-msvc] in
projects built with MSVC using the officially [recommended way][use-msvc],
i.e. by importing the `wxwidgets.props` file.

If your project does this, its workflow on GitHub Actions simply needs to add

```yaml
      - name: Set up wxWidgets
        uses: wxWidgets/setup-wxwidgets-msvc@v1
        with:
          ref: v3.3.4
```

to its job and then it can just use

```yaml
      - name: Set up MSBuild
        uses: microsoft/setup-msbuild@v3

      - name: Build
        run: |
          msbuild -noLogo -maxCpuCount `
            -property:Configuration=Release -property:Platform=x64 `
            MyProject.sln
```

to build the project itself.

See the [action README][readme] for more information about the other possible
inputs (notably `toolset` which should be set if the project doesn't use the
default one for the image), but the above is enough for many cases and takes
care of building wxWidgets and, importantly, caching it for the subsequent
builds, so that it won't be rebuilt every time the application is built.


[setup-wx-msvc]: https://github.com/wxWidgets/setup-wxwidgets-msvc/
[use-msvc]: https://docs.wxwidgets.org/3.3/plat_msw_install.html#msw_build_apps_msvc
[readme]: https://github.com/wxWidgets/setup-wxwidgets-msvc/#usage
