# Gocorpora
A simple Golang interface for Darius Kazemi's Corpora Project, "a collection of static corpora (plural of 'corpus') that are potentially useful in the creation of weird internet stuff." The gocorpora interface makes it easy to use data from the Corpora Project in your program. Here's an example of how it works:

```go
package main

import (
	"fmt"
	"encoding/json"
	"github.com/artikell/gocorpora"
)

func main() {
	corporationsNewspapersText := `{
  "description": "A list of newspapers scraped in early 2013.",
    "newspapers":
      [
        "The Wall Street Journal"
      ]
}`
	data := gocorpora.DataCorporationsNewspapers{}
	err := json.Unmarshal([]byte(corporationsNewspapersText), &data.Data)
	if err != nil {
		panic("json unmarshal error:" + err.Error())
		return
	}
	fmt.Printf("json unmarshal success, val: %+v\n", data)
}
```

### Tips

We wrap a layer of `data` structure in front of the whole data to process the data of JSON array, example: [corpora/australia.json at master · dariusk/corpora](https://github.com/dariusk/corpora/blob/master/data/societies_and_groups/designated_terrorist_groups/australia.json)

## Installation

Installation by hand:
```shell
go get github.com/artikell/gocorpora
```
## Update

The current project will synchronize the data of the [dariusk/corpora](https://github.com/dariusk/corpora) project and generate a new model at 2 o'clock every day through the action function of GitHub

## Acknowledgements

Thanks to Darius Kazemi and all of the Corpora Project contributors!

