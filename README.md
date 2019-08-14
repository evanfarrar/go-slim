# go-slim

[![codecov](https://codecov.io/gh/mattn/go-slim/branch/master/graph/badge.svg)](https://codecov.io/gh/mattn/go-slim)
[![Build Status](https://travis-ci.org/mattn/go-slim.png?branch=master)](https://travis-ci.org/mattn/go-slim)
[![GoDoc](https://godoc.org/github.com/mattn/go-slim?status.svg)](http://godoc.org/github.com/mattn/go-slim)

slim template engine for golang

## Features

* Small Virtual Machine

  Enough to manipulate object in template. Support Number/String/Function/Array/Map.

* Ruby Like Text Rendering

  Support `Hello #{"Golang"}`

## Usage

### Template File

```slim
doctype 5
html lang="ja"
  head
    meta charset="UTF-8"
    title
  body
    ul
    - for x in foo
      li = x
```

### Your Code

```go
tmpl, err := slim.ParseFile("template.slim")
if err != nil {
	t.Fatal(err)
}
err = tmpl.Execute(os.Stdout, slim.Values{
	"foo": []string{"foo", "bar", "baz"},
})
```

### Output

```html
<!doctype html>
<html lang="ja">
  <head>
    <meta charset="UTF-8"/>
    <title>
    </title>
  </head>
  <body>
    <ul>
      <li>foo</li>
      <li>bar</li>
      <li>baz</li>
    </ul>
  </body>
</html>
```

## Builtin-Functions

* trim(s)
* to_upper(s)
* to_lower(s)
* repeat(s, n)

## License

MIT

## Author

Yasuhiro Matsumoto (a.k.a. mattn)
