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
