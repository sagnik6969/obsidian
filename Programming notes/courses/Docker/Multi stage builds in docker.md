- Sometimes we only need some code while compiling. We don't need that code for running the app.
- So we can reduce the image size by deleting the extra code.
- Multistage builds are required for this.
- `COPY --from=build /bin/hello /bin/hello`  `=>` to copy from previous build.
- 

#### Example
```Dockerfile
# syntax=docker/dockerfile:1
FROM golang:1.21 as build 
WORKDIR /src
COPY <<EOF /src/main.go
package main

import "fmt"

func main() {
  fmt.Println("hello, world")
}
EOF
RUN go build -o /bin/hello ./main.go

FROM scratch
COPY --from=build /bin/hello /bin/hello  # to copy from previous build
CMD ["/bin/hello"]
```