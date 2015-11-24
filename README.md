# go-slackcat-writer

A Go package for sending messages to a Slack channel using a standard io.Writer interface

## Usage

```
package main

import (
	"flag"
	"github.com/whosonfirst/go-slackcat-writer"
	"strings"
)

func main() {

	var channel = flag.String("config", "", "The path to your Slackcat config file")

	flag.Parse()
	args := flag.Args()

	w, err := slackcat.NewWriter(*config)

	if err != nil {
		panic(err)
	}

	msg := strings.Join(args, " ")

	b := []byte("Write " + msg)

	_, err = w.Write(b)

	if err != nil {
		panic(err)
	}

	_, err = w.WriteString("WriteString " + msg)

	if err != nil {
		panic(err)
	}
}
```

## Caveats

* https://github.com/whosonfirst/slackcat
