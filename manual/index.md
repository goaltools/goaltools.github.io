---
layout: manual
title: Introduction to Goal
---
> Goal is a set of independent utilities that may be used together or separately.
> All of them form a full stack MVC (Model - View - [Controller](handlers/controllers.html)) web framework.
>
> The list of currently available utilities includes:
>
> * [`goal new`](new/) creates a new skeleton application with opinionated [structure](new/index.html#default-layout) and parameters.
> This is a command for easy and fast start of a new project.
> * [`goal run`](run/) runs a file watcher / task runner that is responsible for (re)compilation / (re)start  of your project and,
> if neccessary, (re)build of client-side assets. [Configuration file](run/index.html#configuration-file) is used to describe how
> to compile, build, start things.
> * [`goal generate handlers`](handlers/) generates a package with HTTP handler functions from your
> [controllers](handlers/controllers.html). The generated package is fully compatable with the standard library
> and thus can be used with any router.

## Getting started
To get started with Goal, first install it:

```bash
go get -u github.com/colegion/goal
```

After you have the Toolkit installed, create a new project.
`path/to/your/project` must not exist at the time of running this command:

```bash
goal new path/to/your/project
```

**Please, note that both Goal toolkit and your project (during development) must be
located within [`$GOPATH/src`](https://golang.org/cmd/go/#hdr-GOPATH_environment_variable) directory.**


To start the project you have just created use:

```bash
goal run path/to/your/project
```

Gongratulations, your skeleton app is ready and running. Start making changes.
Open `http://127.0.0.1:8080` to view results.
