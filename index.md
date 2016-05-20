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
```yaml
```
