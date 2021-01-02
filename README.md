# loop
Object-Oriented programming in comes to Lua.

loop implements basic oop patterns in pure lua

loop mainly written for LuaJIT, but also supports basic lua versions(particually, explained below).

## Examples

### class(class_name: string): (ext: string,table) -> tail
Class is a lua table with specific meta-methods defined.
Each call of the `class` function changes the environment to the class table, so we can write code as shown below. Each call of this function must be followed by a call of the `close` function.

 ```lua
class "Person" do
  function init(self, name)
    self.name = name
  end
  function greets()
    print("Hi, "..self.name)
  end
end close()

person = Person.new "Tolya"

person.greets() --> Hi, Tolya
 ```

Classes can be extended as many times as you want
```lua
class "A" do 
 a = 1 
end close()

class "B" do
 b = 2 
end close()

class "C" "A" "B" do
 function init() 
  print(a,b) 
 end
end close()

insc = C.new() --> 1,2
```

Classes can contain an infinite number of nested classes
```lua
class "A" do
 class "Inner" do
  i = 1
 end close()
end close()

print(A.Inner.i) --> 1
```
