## Which one below is not one of the logical operators of Go?
1. `||`
2. `!=` *CORRECT*
3. `!`
4. `&&`

> **2:** That's the "not equal" operator. It's a comparison operator, not a logical operator.


## Which one of these types is returned by a logical operator?
1. int
2. byte
3. bool *CORRECT*
4. float64

> **3:** That's right. All the logical operators return an untyped bool value (true or false).


## Which one of these can be used as an operand to a logical operator?
1. int
2. byte
3. bool *CORRECT*
4. float64

> **3:** That's right. All the logical operators expect a bool value (or a bool expression that yields a bool value).


## What does this program print?
```go
package main
import "fmt"

func main() {
    var (
        on  = true
        off = !on
    )

    fmt.Println(!on && !off)
    fmt.Println(!on || !off)
}
```

1. true true
2. true false
3. false true *CORRECT*
4. false false
5. error

> **3:** `!on` is false. `!off` is true. So, `!on && !off` is false. And, `!on || !off` is true.


## What does this program print?
```go
package main
import "fmt"

func main() {
    on := 1
    fmt.Println(on == true)
}
```

1. true
2. false
3. error *CORRECT*

> **3:** `on` is int, while `true` is a bool. So, there's a type mismatch error here. Go is not like other C based languages where `1` equals to `true`.


## What does this code print?
```go
// Note: "a" comes before "b"
a := "a" > "b"
b := "b" <= "c"
fmt.Println(a || b)
```

1. "a"
2. "b"
3. true *CORRECT*
4. false
5. error

> **1-2:** Logical operators return a bool value only.

> **3:** Order is like so: "a", "b", "c". So, `"a" > "b"` is false. `"b" <= "c"` is true. So, `a || b` is true.

> **5:** There isn't an error. Strings are actually numbers, so, they're ordered and can be compared using the ordering operators.


## What does the following program print?
```go
// Let's say that there are two functions like this:
//
//   super() which returns true and prints "super ".
//   duper() which returns false and prints "duper ".
//
// Remember: Logical operators short-circuit.

package main
import "fmt"

func main() {
    _ = duper() && super()
    _ = super() || duper()
}

// Don't mind about these functions.
// Just focus on the problem.
// These are here just for you to understand it better.
func super() bool {
    fmt.Print("super ")
    return true
}

func duper() bool {
    fmt.Print("duper ")
    return false
}
```

1. "super duper super duper"
2. "duper super"
3. "duper super duper super"
4. "super duper"

> **1, 3:** Remember: Logical operators short-circuit.

> **2:** That's right.
> 
> In: `duper() && super()`, `duper()` returns false, so, logical AND operator short-circuits and doesn't call `super()`; so it prints: `"duper "`.
> 
> Then, in: `super() || duper()`, `super()` returns true, so, logical OR operator short circuits and doesn't call `duper()`; so it prints `"super "`.

> **4:** Think again.

Example program is [here](https://play.golang.org/p/C-syhwgXSx2).