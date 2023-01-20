---
title: Functional programming in Erlang
date: 2022/01/20
description: My initial thoughts on functional and concurrent programming. 
tag: erlang, functional programming
author: Niklas Enberg
---
I just recently started [a course](https://www.su.se/sok-kurser-och-program/ib912c-1.413351) in concurrent and distributed programming at DSV. So far it's been a lot of fun being introduced to the functional programming paradigm.  

The language we are using is called Erlang and is quite old, as it was developed at Ericsson's Computer Science in the late 80's. In spite of this I've found it quite impressive in my usage thus far, and wanted to highlight two features that I find nifty.

## Pattern matching
This enables the implicit extraction of values based on data structure properties and eliminates a lot of boiler-plate.

```java
my_function([Head | Tail]) -> 
    do_something(Head). 
```

This function will take any list consisting of two or more elements, as that is needed to match with the function clause of having both a head and a tail. The function header thereby does a lot of work on it's own, very handy.

## Recursion
Since Erlang is a declarative language, recursion is used instead of iteration. Coming from an object-oriented background this was somewhat confusing at first, but it sure has grown on me. This is easily demonstrated by examining a method which looks at characters in a string, and maps it to it's number of occurences:

### Java
```java
public static Map<Character, Integer> countCharacters(String str) {
        HashMap<Character, Integer> result = new HashMap<>();

        if (str.isEmpty()) {
            return result;
        }

        for (Character c : str.toCharArray()) {
            if (result.containsKey(c)) {
                result.put(c, result.get(c) + 1);
            } else {
                result.put(c, 1);
            }
        }

        return result;
    }
```

### Erlang
```java
count_characters(Str) -> count_characters(Str, #{}).
count_characters([], M) -> M;
count_characters([H | T], M) ->
  case maps:is_key(H, M) of
    true -> count_characters(T, maps:put(H, maps:get(H, M) + 1, M));
    false -> count_characters(T, maps:put(H, 1, M))
  end.
```

Although the imperative (Java) approach is crystal clear as to what the code does, the declarative (Erlang) approach gives a concise overview in far less LoC. Thinking in a recursive manner can be hard to get used to, but I often find it produces more robust solutions.

I look forward to learning more functional programming and combining it with large scale distribution, as that is Erlang's strong suite. 

P.S

[Erlang: The Movie](https://www.youtube.com/watch?v=xrIjfIjssLE) should've won the Palme d'Or.

