---
layout: index
title: High productivity web-development in Go language
---
## Overview

### Controllers and Actions
> Tool `goal generate handlers` generates standard HTTP handler functions out
> of your controllers and actions. The result is a separate package that is compatible
> with the `net/http` MUX.

```go
// Application is a sample controller.
type Application struct {
	*Controller
}

// Greet is a demo action that gets name of a user and renders
// a greeting page.
func (c *Application) Greet(name string) http.Handler {
	c.Context["name"] = name
	return c.Render()
}
```

### Routes & Reverse Routes
> Tool `goal generate routes` scans your HTTP handler functions & their
> comments and produces 2 separate packages:
> the one that provides a slice of routes and handler functions associated
> with them; and a package that can be used to return URN by
> controller & action name in a type safe manner.

```go
// @get /home
func (c *Application) Index() http.Handler {
	return c.Redirect(routes.Account.SignIn(123))
}

// @post /signin/:method
func (c *Application) SignIn(method int) http.Handler {
	...
}
```

### Hot Reloader
> Tool `goal run` uses the rules from `goal.yml` file in the root of your project
> to compile, start your app, and hot reload it when some changes are made to the code.

```yaml
init:
  - npm install coffeescript # Install CoffeeScript.
watch:
  ./controllers*:            # Watch "./controllers" and its subdirectories.
    - /run buildApp          # Rebuild the app on change.
    - /single startApp       # Restart the previously started instance of app.
  ./qwerty:
    - /pass # Do nothing as we haven't decided yet what to do here.
buildApp:
  # Commands for building the project.
  - go build -o ./bin/run:EXT github.com/colegion/sample
startApp:
  - ./bin/run:EXT # A command for start of the app.
```
