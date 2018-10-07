# fmtbytes
A package that makes it easier to read structured bytes from a file.

## Installation
```bash
$ go get github.com/pisdhooy/fmtbytes
```

## basic Example
This example shows how fmtbytes can be used to confirm that a .png file is actually in the .png format.

```go
package main

import (
  "fmt"
  
  "github.com/pisdhooy/fmtbytes"
)

func main() {
  file, err := os.Open("path/to/some.file.png");
  if err != nil {
    panic(err)
  }
  
  highBit := fmtbytes.ReadSingleByte(file);
  if highBit != 89 {
    panic("high bit invalid")
  }
  
  signature := fmtbytes.ReadBytesString(file, 3)
  if signature != "PNG" {
    panic("file signature is invalid")
  }
}
```


