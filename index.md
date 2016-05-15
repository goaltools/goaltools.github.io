---
layout: index
title: A set of tools for high productivity web-development in Go language
---
## Overview

### Controllers and Actions
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

### Routes
```go
// @get /
func (c *Application) Index() http.Handler {
	...
}

// @post /signin/:method
func (c *Application) SignIn(id method) http.Handler {
	...
}
```

### Reverse routes
```go
// Profile is an action that redirects a user to Sign In page
// if he/she is not authorized.
func (c *Account) Profile(id, page int) http.Handler {
	if c.notAuthorized() {
		return c.Redirect(routes.Account.SignIn()) // Reverse route to the Sign In page.
	}
	...
}
```
