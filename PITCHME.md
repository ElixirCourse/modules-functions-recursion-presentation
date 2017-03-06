### Модули, функции и рекурсия

Валентин Михов

#HSLIDE

### Дефиниране на модул

```elixir
defmodule Times do
  def double(n) do
    n * 2
  end
end
```

#HSLIDE

# Компилиране и зареждане на файл

```bash
iex(1)> c "times.exs"
[Times]
iex(2)> Times.double(10)
20
```

#HSLIDE

### Функции с различен брой параметри

```bash
iex(1)> String.split("Elixir is awesome. It totally kicks bum.")
["Elixir", "is", "awesome.", "It", "totally", "kicks", "bum."]

iex(2)> String.split("Elixir is awesome. It totally kicks bum.", ".", parts: 2)
["Elixir is awesome", " It totally kicks bum."]
```

#HSLIDE

### do..end блокове с код

```elixir
def double(n), do: n * 2
```

#HSLIDE

### Дефиниране на функции и pattern matching

```elixir
defmodule Factorial do
  def of(0), do: 1
  def of(n), do: n * of(n - 1)
end
```

#HSLIDE

### Реда на дефиниране на функциите има значение

```elixir
defmodule Factorial do
  def of(n), do: n * of(n - 1)
  def of(0), do: 1
end
```

#HSLIDE

### Guard клаузи при дефиниране на функции

```elixir
defmodule Fibonachi do
  def of(1), do: 1
  def of(2), do: 1
  def of(n) when is_number(n), do: of(n - 1) + of(n - 2)
end
```

#HSLIDE

### Параметри със стойности по подразбиране

```elixir
defmodule Example do
  def func(p1, p2 \\ 2, p3 \\ 3, p4) do
    IO.inspect [p1, p2, p3, p4]
  end
end

Example.func("a", "b") # => ["a", 2, 3, "b"]
Example.func("a", "b", "c") # => ["a", "b", 3, "c"]
Example.func("a", "b", "c", "d") # => ["a", "b", "c", "d"]
```

#HSLIDE

### Private функции

Да решим FizzBuzz проблема стъпка по стъпка

#HSLIDE

Pipe оператора - `|>`

```elixir
iex(30)> Enum.join(
  String.split(
    String.upcase(
      "name,sex,location"),
    ","),
  " "
)
"NAME SEX LOCATION"
```

#HSLIDE

### Pipe оператора - `|>`

```elixir
iex(33)> "name,sex,location"
  |> String.upcase
  |> String.split(",")
  |> Enum.join(" ")
"NAME SEX LOCATION"
```

#HSLIDE

### Връзки между модули и влагане

```elixir
defmodule Outer do
  defmodule Inner do
    def inner_func do
      "hello world"
    end
  end

  def outer_func do
    "Greeting from the inner func: #{Outer.Inner.inner_func}"
  end
end

Outer.outer_func # => "Greeting from the inner func: hello world"
Outer.Inner.inner_func # => "hello world"
```

#HSLIDE

### import

```elixir
defmodule CsvUtils do
  import String

  def upcase_space_transform(csv_line) do
    csv_line
    |> upcase
    |> split(",")
    |> Enum.map(&strip/1)
    |> Enum.join(" ")
  end
end
```

#HSLIDE

### alias

```elixir
defmodule Outer.Inner do
  def inner_func do
    "hello world"
  end
end

defmodule Outer do
  alias Outer.Inner, as: Inner

  def outer_func do
    "Greeting from the inner func: #{Inner.inner_func}"
  end
end
```

#HSLIDE

### require

#HSLIDE

### Модулни атрибути

```elixir
defmodule Greeter do
  @standard_greeting "Hello, stranger!"

  def greet(nil) do
    IO.puts @standard_greeting
  end

  def greet(name) do
    IO.puts "Hello, #{name}!"
  end
end
```

#HSLIDE

### Използване на Erlang модули

```elixir
:rand.uniform(100) # => 98
:rand.uniform(100) # => 41
```

#HSLIDE

### Да попишем малко код :-)

#HSLIDE

### Въпроси?
