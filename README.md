# Calculator

**Calculator sample application from the Groxio OTP course**

## Installation

The file `.tool-versions` for [asdf](https://github.com/asdf-vm/asdf) contains the Elixir version to use: `1.11.1`.

## Playing with the application

Through the `Calculator` module to call the `Boundary` that wraps the non-OTP service process logic:

```elixir
iex(2)> Calculator.add(calculator, 10)
{:add, 10}
iex(3)> Calculator.subtract(calculator, 3)
{:subtract, 3}
iex(4)> Calculator.multiply(calculator, 4)
{:multiply, 4}
iex(5)> Calculator.divide(calculator, 2)
{:divide, 2}
iex(6)> Calculator.state(calculator)
14.0
iex(7)> Calculator.clear(calculator)
:clear
iex(8)> Calculator.state(calculator)
0
```
Or through the `GenServer` which is an implementation of the `Boundary` but using OTP:

```elixir
iex(1)> alias Calculator.Server
Calculator.Server
iex(2)> {:ok, server} = Server.start_link(0)
{:ok, #PID<0.142.0>}
iex(3)> Server.add(server, 10)
:ok
iex(4)> Server.subtract(server, 3)
:ok
iex(5)> Server.multiply(server, 4)
:ok
iex(6)> state = Server.state(server)
28
iex(7)> Server.inc(server)
:inc
iex(8)> Server.negate(server)
:ok
iex(9)> Server.state(server)
-29
iex(10)> Server.clear(server)
:ok
iex(11)> Server.state(server)
0
```
## Running tests

Run `mix test` :

```
➜  calculator (master) ✔ mix test
Compiling 2 files (.ex)
......

Finished in 0.02 seconds
6 tests, 0 failures

Randomized with seed 162315
```
