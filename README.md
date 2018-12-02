# servy
An HTTP Server using Elixir + Erlang/OTP

## Question:

* Is *'world'* same as *"world"*? Seems like it when passing it to `hello` method but passing it to `String.reverse/1` 
throws an error 🤔.

## Notes

### Installation & Setup

* `brew update && brew install erlang && brew install elixir`
* check version: `elixir --version`
* IntelliJ plugin - https://github.com/KronicDeth/intellij-elixir

### mix 

* create a new mix project: `mix new servy`

### iex

* To start an *iex* session: `iex`
* To compile a file in memory within an *iex* session: `c lib/servy.ex`
* To start an *iex* session with just a file: `iex lib/servy.ex`
* To start an *iex* in the context of a *mix* project: `iex -S mix`
* To recompile a module within an *iex* session: `r Servy`
* To get help within an *iex* session: `h <enter>` you can also do `h String.` to get help on *String* module

### Shell History
* *iex* doesn't remember commands from the previous sessions by default unless enabled. Add the following line to your
`.zshrc` or `.bashrc`:
`export ERL_AFLAGS="-kernel shell_history enabled"`

### Pattern Matching
`=` operator is not an assignment operator like in other programming languages but is a match operator 🤯
```
a = 1
> 1
a
> 1
1 = a
> 1 🤯
``` 

Elixir tries to match left with right with the `=` operator, if it does then it returns the matching value. So when
we do `1 = a` the value of a was already assigned to 1 previously, `1 = a` matches both values, hence it returns 1.
If you do `2 = a` then it returns no match error as value of `a` is 1 not 2.

You can reassign a by doing `a = 2` and now if you do `2 = a` then it returns 2. If you only want to check for a match
instead of assigning, you can use a pen `^` operator like so `^a=3` This returns no match error as `a`'s value is 
currently 2 not 3.

#### Destructure using Pattern Matching
```
[first, 2, last] = [1,2,3]
first
> 1
last
> 3
```

Destructuring should match the values on left hand side with **term** on the right unless the values on the left hand side
are replaced with variables in which case variables are mapped to values instead of matching (given the whole thing)
matches in the first place. Also, the arrity on the both sides should match. So, [first, last] = [1, 2, 3] will return
no match error.

If you want to match with anything but don't want to assign it to a variable, you can use an underscore `_`:
`[first, _, last] = [1, 2, 3]`
In this case `first` is assigned 1, `last` is assigned 3. You cannot use `_` as a variable.

* A **term** is a value of any data type: a string, an atom, a map, a list, etc.

* Elixir atoms are prefixed by a colon. Here's a map with atoms as keys: `%{:method => "GET", :path => "/wildthings"`

Which can be rewritten in a more concise way by: `%{method: "GET", path: "/wildthings"}`

This concise way is only allowed if keys are atoms otherwise you have to use the general => form:
%{ "method" => "GET", "path" => "/wildthings" }
