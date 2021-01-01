# loop
Object-Oriented programming in comes to Lua.

loop implemets basic oop patterns in pure lua

loop mainly written for LuaJIT, but also supports basic lua versions(particually, explained below).

## Examples

### class(class_name: string): void
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
