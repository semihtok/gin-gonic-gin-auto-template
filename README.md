[![Go Report Card](https://goreportcard.com/badge/semihtok/gin-gonic-gin-autotemplate)](http://goreportcard.com/report/semihtok/gin-gonic-gin-autotemplate)
[![Build Status](https://travis-ci.org/semihtok/gin-gonic-gin-autotemplate.svg?branch=master)](https://travis-ci.org/semihtok/gin-gonic-gin-autotemplate)
 
# gin-gonic-gin-autotemplate
This little code provides to define your templates automatically when system started.

## Usage
 1. Create ./templates path then put template files in it.
 2. Be sure layout page named as "layout.html" 
 3. Add this method in your code 
 
``` go
func setHtmlPages(router *gin.Engine) {

	templates := multitemplate.New()

	templateDir := "templates/"

	files, _ := ioutil.ReadDir("./templates")

	for _, f := range files {

		if f.Name() != "layout.html" {

			templates.AddFromFiles(strings.Split(f.Name(), ".")[0],
				templateDir + "layout.html",
				templateDir + f.Name())

		}
	}
}
```
 
and call in main method with gin instance

``` go
func main() {
	router := gin.Default()
	setHtmlPages(router)
}
```
 
That's it! 
