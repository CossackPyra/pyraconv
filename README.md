# pyraconv isGo type conversion library

__Example__

  package main
  
  import (
  	"encoding/json"
  	"fmt"
  
  	"github.com/CossackPyra/pyraconv"
  )
  
  func main() {
  
  	arrjson := []string{`{}`,
  		`{"x":"1234557", "u":"http://golang.org/"}`,
  		`{"x":325436, "u":["http://golang.org/", "http://www.golang.org/"]}`}
  
  	for _, json1 := range arrjson {
  		var m1 map[string]interface{}
  		e := json.Unmarshal([]byte(json1), &m1)
  		if e != nil {
  			continue
  		}
  		x := pyraconv.ToInt64(m1["x"])
  		fmt.Println("X:", x)
  		u := pyraconv.ToStringArray(m1["u"])
  		for i1, url := range u {
  			fmt.Println("URL:", i1, url)
  		}
  	}
  
  }

__Result__

  X: 0
  X: 1234557
  URL: 0 http://golang.org/
  X: 325436
  URL: 0 http://golang.org/
  URL: 1 http://www.golang.org/



