---
title: "Getting Started"
date: 2019-11-21T16:15:09+08:00
draft: false
weight: 10
---

## Installation

`go get github.com/leaanthony/clir`

## Basic Usage

```go
package main

import (
	"fmt"

	"github.com/leaanthony/clir"
)

func main() {

	// Create new cli
	cli := clir.NewCli("Flags", "A simple example", "v0.0.1")

	// Name
	var name string
	cli.StringFlag("name", "Your name", &name)
	
	// Define action for the command
	cli.Action(func() error {

		if name == "" {
			name = "Anonymous"
		}
		fmt.Printf("Hello %s!\n", name)

		return nil
	})

	cli.Run()

}
```