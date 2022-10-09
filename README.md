# Go Queue

## Queue

## Library
The library used is "go-datastructures".  
https://github.com/Workiva/go-datastructures  

The library can store values of different types in the same queue.  

Please install as needed.  
$ go get -u github.com/Workiva/go-datastructures/...  

## Code
```Go
package main

import (
	"fmt"
	"strconv"

	"github.com/Workiva/go-datastructures/queue"
)

func main() {

	// Queue Creation
	var queueObj queue.Queue
	// Current queueObj : []

	// Adding values to a queue (this queue library can store multiple types)
	queueObj.Put("AAA")
	queueObj.Put(111)
	queueObj.Put("BBB")
	queueObj.Put(222)
	queueObj.Put("CCC")
	queueObj.Put(333)
	// Current queueObj :  ["AAA", 111, "BBB", 222, "CCC", 333]

	// Get 3 values from the queue
	qObj1, _ := queueObj.Get(int64(3))
	// Current queueObj :  [222, "CCC", 333]

	// Output value
	fmt.Println("From Queue Value : " + qObj1[0].(string) + ", " + strconv.Itoa(qObj1[1].(int)) + ", " + qObj1[2].(string)) // From Queue Value : AAA, 111, BBB

	// Get 3 values from the queue
	qObj2, _ := queueObj.Get(int64(3))
	// Current queueObj :  []

	// Output value
	fmt.Println("From Queue Value : " + strconv.Itoa(qObj2[0].(int)) + ", " + qObj2[1].(string) + ", " + strconv.Itoa(qObj2[2].(int))) // From Queue Value : 222, CCC, 333

	// Queue value check
	if queueObj.Empty() {
		fmt.Println("Queue Object is Empty.") // Queue Object is Empty.
	} else {
		fmt.Println("Queue Object is not Empty.")
	}
	// Current queueObj :  []

	// Adding values to a queue
	queueObj.Put("DDD")
	queueObj.Put(444)
	queueObj.Put("EEE")
	queueObj.Put(555)
	// Current queueObj :  ["DDD", 444, "EEE", 555]

	// Queue value check
	if queueObj.Empty() {
		fmt.Println("Queue Object is Empty.")
	} else {
		fmt.Println("Queue Object is not Empty.") // Queueb Object is not Empty.
	}
	// Current queueObj :  ["DDD", 444, "EEE", 555]

	// Get 2 values from the queue
	qObj3, _ := queueObj.Get(int64(2))
	// Current queueObj :  ["EEE", 555]

	// Output value
	fmt.Println("From Queue Value : " + qObj3[0].(string) + ", " + strconv.Itoa(qObj3[1].(int))) // From Queue Value : DDD, 444
}
```

## Output Sample

$ go run queue.go  
From Queue Value : AAA, 111, BBB  
From Queue Value : 222, CCC, 333  
Queue Object is Empty.  
Queue Object is not Empty.  
From Queue Value : DDD, 444  

$ go build -o queue queue.go  
$ ./queue  
From Queue Value : AAA, 111, BBB  
From Queue Value : 222, CCC, 333  
Queue Object is Empty.  
Queue Object is not Empty.  
From Queue Value : DDD, 444  
