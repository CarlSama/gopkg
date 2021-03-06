# func Append(s Value, x ...Value) Value

参数列表

- s Value    切片数据，类型是 reflect.Value
- x ...Value 切片数据，类型是 reflect.Value

返回值：

- Value 返回新的切片

功能说明：

- 追加一个切片x值到切片，并返回所创建的Slice。在Go中，每一个x值必须是分配给切片的元素类型。

代码实例：
	
	package main
	import (
		"fmt"
		"reflect"
	)
	
	func main(){
		var a []int
		var value reflect.Value = reflect.ValueOf(&a)
		
		//判断指针是否指向内存地址
		if !value.CanSet() {
			value = value.Elem() //使指针指向内存地址
		}
		
		value = reflect.Append(value, reflect.ValueOf(1))
		value = reflect.Append(value, reflect.ValueOf(3), reflect.ValueOf(4)) //支持可变参数
		
		fmt.Println(value.Kind(), value.Slice(0, value.Len()).Interface())
		//>>slice [1 3 4]
	}
