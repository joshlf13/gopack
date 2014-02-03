<!--
Copyright 2014 The Authors. All rights reserved.
Use of this source code is governed by a BSD-style
license that can be found in the LICENSE fil
-->

gopack
======

Bitpacking for Go.

##Usage


```Go
// Define arbitrary structs for packing.
type color struct {
  R, G, B uint8
}

red := color{255, 0, 0}
b := make([]byte, 3)
gopack.Pack(b, red)

// Use field tags to specify custom bit widths.
type unixMode struct {
  User, Group, Other uint8 `gopack:"3"`
}

// Embed structs nested arbitrarily deep.
type file struct {
  Size uint32
  Mode unixMode
}

// Unexported fields are ignored.
type person struct {
  name string
  Age uint8
}

// Use int types and bool types.
type fileHandle struct {
  File file
  Open bool
  Seek uint32
}
```

##Documentation

See the [documentation](http://godoc.org/github.com/joshlf13/gopack).