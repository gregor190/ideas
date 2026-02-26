# Hello Language Specification

## Overview
Hello is a playful scripting language designed with Flex and Bison.  
It blends Python-like syntax with socket rituals and f-string engines.

## Features
- **Variables**: `var = "string"`
- **Print**: `print(f"text {var}")`
- **F-strings**: `fa = f"embedded {var}"`
- **Sockets**:
  - Creation: `socket = listen tcp://127.0.0.1:8080`
  - Default state: closed
  - Lifecycle:
    - `socket.open()`
    - `socket.close()`
    - `socket.delete()`
- **Comments**: `# this is a comment`
- **Input**: `username = input("Enter text: ")`
- **Functions**:  
  ```hello
  def myfunc(arg1, arg2):
      print(f"args {arg1} {arg2}")
<h2>Protocols</h2>

Supported protocols: TCP and UDP.
Default port: 80 if unspecified.
