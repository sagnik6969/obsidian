1. `int $v1;` => if we specify type to a variable then the type cant be changes.
2. `$v1 = 0` => if we don't specify type then type can be changed.
3. we can specify types of a function input type. If the input argument doesnot match then an error will occur.
```
class Test

{
    public int $v1;
    public int $v2;
    public function __construct()
    {
       $this->v1 = 0;
        $this->v2 = 11111;
    }
}

function f(Test $x)
{
    var_dump($x->v1);
}
f(12);
```
=> the above code will give an error.