Сборка и запуск простой проги на Go
источник
https://go.dev/doc/code

сщздать и инициализировать проект:
$ mkdir hello # Alternatively, clone it if it already exists in version control.
$ cd hello
$ go mod init example/user/hello
$ cat go.mod
module example/user/hello
...

создать файл hello.go с main:
package main
import "fmt"
func main() {
	fmt.Println("Hello, world.")
}

инсталировать:
$ go install example/user/hello
в рабочей директории можно
$ go install .
$ go install

на етом этапе уже можно скомпилировать и вызвать
$ go build hello.go
$ ./hello

добавить в путь и вызвать
$ export PATH=$PATH:$(dirname $(go list -f '{{.Target}}' .))
$ hello
Hello, world.

можно проинициализировать гит
$ git init
$ git add ...
$ git commit ...

Импорт пакетов из своего модуля
$HOME/hello/morestrings/reverse.go
package morestrings
...
$ cd $HOME/hello/morestrings
$ go build

$HOME/hello/hello.go
...
import (
	....
	"example/user/hello/morestrings"
)
...

$  go install example/user/hello
$ hello


Импорт пакетов из удаленных модулей:
