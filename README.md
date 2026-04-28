# push_swap (42)

**EN:** `push_swap` is a sorting project from 42 School. The goal is to sort a stack of integers using a limited set of operations and output the smallest possible number of moves.

**ES:** `push_swap` es un proyecto de ordenación de 42. El objetivo es ordenar una pila de enteros usando un conjunto limitado de operaciones e imprimir el menor número posible de movimientos.

---

## Contents / Contenido

- [Requirements / Requisitos](#requirements--requisitos)
- [Build / Compilación](#build--compilación)
- [Usage / Uso](#usage--uso)
- [Operations / Operaciones](#operations--operaciones)
- [Algorithm / Algoritmo](#algorithm--algoritmo)
- [Input validation / Validación de entrada](#input-validation--validación-de-entrada)
- [Project structure / Estructura del proyecto](#project-structure--estructura-del-proyecto)

---

## Requirements / Requisitos

**EN**
- A Unix-like environment (Linux/macOS)
- `cc` compiler
- `make`

**ES**
- Entorno tipo Unix (Linux/macOS)
- Compilador `cc`
- `make`

---

## Build / Compilación

**EN / ES**
```bash
make
```

This will build:
- `push_swap` (main program)

To clean:
```bash
make clean
```

To full clean (including binary):
```bash
make fclean
```

Rebuild:
```bash
make re
```

---

## Usage / Uso

### Basic / Básico

**EN**
`push_swap` prints to `stdout` the sequence of operations needed to sort the numbers.

**ES**
`push_swap` imprime por `stdout` la secuencia de operaciones necesarias para ordenar los números.

```bash
./push_swap 2 1 3
./push_swap "2 1 3"
```

### Check number of moves / Ver número de movimientos

```bash
./push_swap 2 1 3 | wc -l
```

### Verify with checker (Linux) / Verificar con checker (Linux)

**EN**
This repository includes a `checker_linux` binary you can use to validate the output:

```bash
ARG="4 67 3 87 23"; ./push_swap $ARG | ./checker_linux $ARG
```

It should print `OK` if the operations correctly sort the stack, otherwise `KO`.

**ES**
Este repositorio incluye el binario `checker_linux` para validar la salida:

```bash
ARG="4 67 3 87 23"; ./push_swap $ARG | ./checker_linux $ARG
```

Debería imprimir `OK` si las operaciones ordenan correctamente la pila, si no `KO`.

---

## Operations / Operaciones

**EN**
The program uses the standard `push_swap` operations:

- `sa`, `sb`, `ss` — swap top two elements
- `pa`, `pb` — push top element between stacks A and B
- `ra`, `rb`, `rr` — rotate (top becomes bottom)
- `rra`, `rrb`, `rrr` — reverse rotate (bottom becomes top)

**ES**
El programa usa las operaciones estándar de `push_swap`:

- `sa`, `sb`, `ss` — intercambia los dos primeros
- `pa`, `pb` — empuja el elemento superior entre pilas A y B
- `ra`, `rb`, `rr` — rota (arriba pasa abajo)
- `rra`, `rrb`, `rrr` — rota inverso (abajo pasa arriba)

---

## Algorithm / Algoritmo

**EN**
This implementation chooses different strategies depending on the input size:
- Small cases: dedicated sorts for 2, 3 and 5 elements
- Larger cases: **chunk-based sorting** (sending ranges to stack B and rebuilding stack A)

**ES**
Esta implementación elige estrategias según el tamaño:
- Casos pequeños: ordenaciones específicas para 2, 3 y 5 elementos
- Casos grandes: **ordenación por “chunks”** (enviando rangos a la pila B y reconstruyendo la pila A)

> Note / Nota: The exact performance depends on the chunk size and input distribution.

---

## Input validation / Validación de entrada

**EN**
The program validates:
- Only integers are accepted
- No duplicates
- Values must fit in 32-bit signed integer range (`INT_MIN` to `INT_MAX`)
- On error, it prints `Error` to `stderr`

**ES**
El programa valida:
- Solo acepta enteros
- No permite duplicados
- Los valores deben estar en rango de `int` (32 bits con signo, `INT_MIN` a `INT_MAX`)
- En error, imprime `Error` por `stderr`

---

## Project structure / Estructura del proyecto

**EN / ES (overview)**
- `src/` — main source code (parsing, operations, sorting)
- `inc/` — headers (`push_swap.h`)
- `libft/` — 42 libft
- `ft_printf/` — custom printf
- `checker_linux` — checker binary for Linux

---

## Author / Autor

- `brturcio`
