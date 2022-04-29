# Underthehood

## Introduction

This library provides LiveView components offering interactive IEx terminals. This allows
peeking 'under the hood' of your application - right in your web browser.

Here's an example of what the `Underthehood.terminal_button/1` component looks
like in practice:

!(Video showing Underthehood in action)[https://raw.githubusercontent.com/frerich/underthehood/main/underthehood-demo.mov]

## Installation

1. Add `underthehood` to your project dependencies.

2. Register a Phoenix hook by editing the `app.js` script of your Phoenix project. This typically
amounts to registering a hook along these lines:
```javascript
import TerminalHook from "../../deps/underthehood/lib/hook"

let Hooks = {}
Hooks.Terminal = TerminalHook

let csrfToken = document.querySelector("meta[name='csrf-token']").getAttribute("content")
let liveSocket = new LiveSocket("/live", Socket, {params: {_csrf_token: csrfToken}, hooks: Hooks})
```

3. In your templates, start using any of the offered LiveView components, e.g.
```elixir
[..]
  def render(assigns) do
     ~H"""
     <div>
       Hello World!
       This is a LiveView!
       <.terminal_button/>
     </div>
     """
   end
[..]
```

## Credits

This library was written by [Frerich Raabe](mailto:frerich.raabe@gmail.com), however it
is really just standing on the shoulders of giants:

* [Phoenix LiveView](https://github.com/phoenixframework/phoenix_live_view) is what enables the interactivity
* [Xterm.js](https://xtermjs.org/) provides the frontend terminal component
* [extty](https://hexdocs.pm/extty/readme.html) is the Elixir package used for running the Elixir shell
