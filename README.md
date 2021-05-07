# pprof

[![GoDoc](https://godoc.org/github.com/things-go/pprof?status.svg)](https://godoc.org/github.com/things-go/pprof)
[![Go.Dev reference](https://img.shields.io/badge/go.dev-reference-blue?logo=go&logoColor=white)](https://pkg.go.dev/github.com/things-go/pprof?tab=doc)
[![Build Status](https://travis-ci.com/things-go/pprof.svg)](https://travis-ci.com/things-go/pprof)
[![codecov](https://codecov.io/gh/things-go/pprof/branch/master/graph/badge.svg)](https://codecov.io/gh/things-go/pprof)
![Action Status](https://github.com/things-go/pprof/workflows/Go/badge.svg)
[![Go Report Card](https://goreportcard.com/badge/github.com/things-go/pprof)](https://goreportcard.com/report/github.com/things-go/pprof)
[![Licence](https://img.shields.io/github/license/things-go/pprof)](https://raw.githubusercontent.com/things-go/pprof/master/LICENSE)
[![Tag](https://img.shields.io/github/v/tag/things-go/pprof)](https://github.com/thinkgos/requestid/tags)

gin pprof middleware

> Package pprof serves via its HTTP server runtime profiling data in the format expected by the pprof visualization tool.

## Usage

### Start using it

Download and install it:

```bash
    go get github.com/things-go/pprof
```

Import it in your code:

```go
    import "github.com/things-go/pprof"
```

### Example

[embedmd]:# (_example/main.go go)
```go
package main

import (
	"github.com/gin-gonic/gin"

	"github.com/things-go/pprof"
)

func main() {
	router := gin.Default()
	pprof.Router(router)
	router.Run(":8080")
}
```

### Use the pprof tool

Then use the pprof tool to look at the heap profile:

```bash
    go tool pprof http://localhost:8080/debug/pprof/heap
```

Or to look at a 30-second CPU profile:

```bash
    go tool pprof http://localhost:8080/debug/pprof/profile
```

Or to look at the goroutine blocking profile, after calling runtime.SetBlockProfileRate in your program:

```bash
    go tool pprof http://localhost:8080/debug/pprof/block
```

Or to collect a 5-second execution trace:

```bash
    wget http://localhost:8080/debug/pprof/trace?seconds=5
```
