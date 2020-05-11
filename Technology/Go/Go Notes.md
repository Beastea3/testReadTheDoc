# Go Notes
**The first step of my journey with Go**.

Firstly, I need to have a macro view of this language, it's advantages and limitation.

[https://hackernoon.com/Go-the-highest-paying-technology-to-know-9c6089d7081d](https://hackernoon.com/golang-the-highest-paying-technology-to-know-9c6089d7081d)

A Space-Themed Intro to Go

Go developers are the top paid in 2017, I think this probably because Google's salary is much higher than
others and Google has hired many Go developers.

Go is a well thought out modern language that utilizes many of the best practices of programming languages created before it.
This is an extremely positive evaluation.

Which Similars to my consideration is that learning go will enable me to touch the root of this field,
in other words, go deeper.

Unlike JS which I use in my work, Go has original type definition, which I think is very useful in the backend server.

the map is also a way to create objects, but with the map, each key or value must be one exact type.

make(map[string]int), keys in string and values in int

defer: In the article, the author calls it to stack, but it's not clear enough, so, will dig more after this article.

%v will replace by default value and %T will replace by type of value.

## Compile
`GOOS=linux GOARCH=amd64 go build` will generate a binary executable file which can run on 64-bit Linux.

## Deployment
The deployment is simpler, use system.d to maintain the app, first time for me to use this feature of Linux, awesome. View [Deploying Go Apps with Systemd in 10 Minutes (without Docker)](https://jonathanmh.com/deploying-go-apps-systemd-10-minutes-without-docker/)for more.

* Create your service file in `/lib/systemd/system/yourapp.service`
* Insert the code below to your service file
```
[Unit]
  Description=yourapp // The name of your app

```

```
[Service]
  Type=simple
  Restart=always // Always restart when your app crashed
  Environment=PORT=9999 // environment variables (optional)
  Environment=MODE=release // environment variables (optional)
  RestartSec=5s
  ExecStart=/somePath/yourapp // your executable file location
[Install]
  WantedBy=multi-user.target 
```
Then we can type `service yourapp start` in command line to start your app. If you want to start it when boot, use `service yourapp enable`.
* Install NginX to reverse proxy the request from 80 to the port which your app use.
```
Edit NginX.conf to make sure you can access your app, some details should be mentioned:```
gzip on;
gzip_disable "msie6";

```

```
gzip_vary on;
gzip_proxied any;
gzip_comp_level 6;
gzip_buffers 16 8k;
gzip_http_version 1.1;
gzip_min_length 256;
gzip_types text/plain text/css application/json application/x-javascript text/xml application/xml application/xml+rss text/javascript application/vnd.ms-fontobject application/x-font-ttf font/opentype image/svg+xml image/x-icon;
```
And if you need to serve a static file such as `index.html`, you need to add lines below to make it happen:
```
// the root you defined in NginX, the other files will be loaded in this path
root /home/somePath/; 
```

```
// the static file which you need to serve, in the path above
server {
  index index.html; 
}
```


## 2018.08.03
Now I have completed the project prototype of my first go-gin web server, but I find there are still some blind-points for me to have a basic learning of this language. So I plan read a basic introduction of Go.

comment in Go is similar to JS.

```
// single-line comment
/*
    multi-line comment
 */
```

data types:
1. boolean True or False;
2. int, float32, float64;
uint8, uint16, uint32, uint64, int8, int16, int32, int64,
uint with no positive or negative. complex128 64 bits complex number;
3. string UTF-8 unicode;
4. some others:
pointer, array, struct, channel, func, interface, map...

Various types of variable defining:

```go
   var vname1, vname2, vname3 type
    vname1, vname2, vname3 = v1, v2, v3

    var vname1, vname2, vname3 = v1, v2, v3
    vname1, vname2, vname3 := v1, v2, v3

    var (
        vname1 v_type1
        vname2 v_type2
    )
```

what is awesome that, if u want to switch two values in 2 variables, u can simply `a, b := b, a`. So neat.

iota 1 increment per const...

```go
package main

import "fmt"
const (
    i=1<<iota
    j=3<<iota
    k
    l
)

func main() {
    fmt.Println("i=",i)
    fmt.Println("j=",j)
    fmt.Println("k=",k)
    fmt.Println("l=",l)
}
```

the result of the code above is

```go
i= 1
j= 6
k= 12
l= 24
```

go equal, `a == b`;

logical operation is same to JS

new feature in go:

```go
package main

import "fmt"

func main() {
   var c1, c2, c3 chan int
   var i1, i2 int
   select {
      case i1 = <-c1:
         fmt.Printf("received ", i1, " from c1\n")
      case c2 <- i2:
         fmt.Printf("sent ", i2, " to c2\n")
      case i3, ok := (<-c3):  // same as: i3, ok := <-c3
         if ok {
            fmt.Printf("received ", i3, " from c3\n")
         } else {
            fmt.Printf("c3 is closed\n")
         }
      default:
         fmt.Printf("no communication\n")
   }
}
```

In the guide, it says select will choose one fit case randomly... So be attention when multiple cases fit.

goto: be able to go to a specific line in a loop;

closure in go:

```go
package main

import "fmt"

func getSequence() func() int {
   i:=0
   return func() int {
      i+=1
     return i  
   }
}

func main(){
   /* nextNumber 为一个函数，函数 i 为 0 */
   nextNumber := getSequence()  

   /* 调用 nextNumber 函数，i 变量自增 1 并返回 */
   fmt.Println(nextNumber())
   fmt.Println(nextNumber())
   fmt.Println(nextNumber())

   /* 创建新的函数 nextNumber1，并查看结果 */
   nextNumber1 := getSequence()  
   fmt.Println(nextNumber1())
   fmt.Println(nextNumber1())
}

```

the pointer is the one which I never used before, does Js have some pointer features?

in Go, & operator is to show the address of the value, and * is to show the value of an address.

and nil is the default value in a defined value but has not been assigned.

### Here is a little episode...
When I looked for some solutions to my go-gin developing, I found a very funny title:  _Understand Go pointers in less than 800 words or your money back_，As a coder whose major is not CS, I'm actually not familiar with such things. So I wrote something here to record something I think about when I read this article.

In Go, there is a pointer type, which I have mentioned before. Textbook explanation of pointer is a value which points to the address of another.

The beginning of the article is about memory, which is common sense... The author said the variable name is an alphanumeric pseudonym for a memory location, Interesting.

Then, in the middle of the article, the author finally began to talk about the pointer. A new definition is: _"A pointer is a value that points to the memory of another variable"_, this is still ambiguous, fortunately, there are some codes to show the pointer.

```go
   func main() {
      a := 200
      b := &a
      *b++
      fmt.Println(a)
   }
```

1. In this simple func, we firstly declare a variable a, then we assign it the value 200, this is easy to understand;
2. We declare b after the a, and assign it as a's address, & symbol is just like a record of a variable, get the address of the variable;
3. The third line is confusing, just as the article says. I have not learnt C before, so I don't know if this is a feature that only Go has. this line is to add 1 to a variable. cus we just store the a's address in b, so we have to use `*` to get the value in that address.(Make sense here, but still don't know why this operations required, why not just add a?)

This is all about the article, do not understand entirely still. But I can not agree more with the saying in the conclusion:_", forming a mental model of how variables and pointers relate takes time and practice."_.

### Vendor
With the release of Go 1.5, there is a new way to discover go packages, and after version 1.6, this feature has been set on as default.

The method came up with 1.5 has no changes to the Go language or the GO compilers, packages are still required to reside in GOPATH, but the vendor can also be a path to be imported from.

Two general guidelines:

* If you vendor a single package, you probably want to vendor all your dependencies;

* Flatted vendor structure will be more adorable;

There are many tools to use the vendor today. `govendor`, `godep` and newly comer `dep`. In my private preference, `dep` will be a good tool for me, it seems more native.

## Effective Go

### Formatting

In most languages, formatting issues are always a contentious problem. In Javascript, I am used to formatting the code in EsLint, which is not official util to format. However, in Go, we have `gofmt`, with which we can ignore the formatting issues and just enjoy our coding. `gofmt` will do everything related to formatting for you.

Something should be paid attention is that parentheses are used not so usually as JS or other languages, control structures like `if`, `for` and `switch` do not have parentheses. What’s more, **Operator precedence is what the spacing implies**, this is different from other languages. In JavaScript and most other languages, even in mathematics, we use parentheses to imply the precedence.

### Functions

Functions in go are unusual.

**Multiple Returns**

This is one of Go’s unusual features, this is aimed to overcome a couple of clumsy idioms in C programs: in-band error returns.

**Named Result Parameters**

Defined the return when defining the function, and use `return` w/o arguments.

Eg:
```go
func ReadFull(r Reader, buf []byte) (n int, err error) {
    for len(buf) > 0 && err == nil {
        var nr int
        nr, err = r.Read(buf)
        n += nr
        buf = buf[nr:]
    }
    return
}
```


**Defer**

Defer schedules a function call to be run immediately before the function executing the defer returns. Effective to deal with resource release.

Eg:

```go
// Contents returns the file's contents as a string.
func Contents(filename string) (string, error) {
    f, err := os.Open(filename)
    if err != nil {
        return "", err
    }
    defer f.Close()  // f.Close will run when we're finished.

    var result []byte
    buf := make([]byte, 100)
    for {
        n, err := f.Read(buf[0:])
        result = append(result, buf[0:n]...) // append is discussed later.
        if err != nil {
            if err == io.EOF {
                break
            }
            return "", err  // f will be closed if we return here.
        }
    }
    return string(result), nil // f will be closed if we return here.
}

```

### `new` And `make`

Both of them are allocation primitives for Go. But they are different and they apply for different things. `make` creates slices, maps, and channels only, and `new` is a more commonly used method of construction.

```go
var p *[]int = new([]int)       // allocates slice structure; *p == nil; rarely useful
var v  []int = make([]int, 100) // the slice v now refers to a new array of 100 ints

// Unnecessarily complex:
var p *[]int = new([]int)
*p = make([]int, 100, 100)

// Idiomatic:
v := make([]int, 100)

```

### Constants

> `1<<3` is a constant expression, while `math.Sin(math.Pi/4)` is not because of the function call to `math.Sin` needs to happen at run time.  

### The init function

> A type of niladic function which is called after all the variable declarations in the package have evaluated their initializers, and those are evaluated only after all the imported packages have been initialized.  

