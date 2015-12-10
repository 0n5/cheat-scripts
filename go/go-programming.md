Go Programming
==============

will not compile if imports missing or there are unused packages<br>
// this is a comment in go //


#### $GOPATH

	$ nano ~/.bash_profile

add to the file:
	
	export GOPATH="$HOME/your-workspace-dir/" 

	$ source ~/.bash_profile



#### Formatting

goimports, adds or removes imports in go file

	$ go get golang.org/x/tools/cmd/goimports



#### Hello World

	$ nano hello.go

``` golang

package main 
import "fmt"

func main() {
	fmt.Println("hello")	
}

```

Compile Source code:

	$ go run hello.go


Build and run executable binary

	$ go build hello.go
	$ ./hello.go
