# XOR STARTER
###### Solved by @imswen
>Este é um desafio de CTF focado em decodificação com operações lógicas.
## About the Challange
Ao acessar o desafio, somos apresentados à seguinte instrução:
>Given the string **label**, **XOR** each character with the integer **13**. Convert these integers back to a string and submit the flag as **crypto{new_string}**.

- [Página do desafio](https://cryptohack.org/courses/intro/xor0/)

Ou seja, temos que aplicar uma operação XOR em cada caractere da string fornecida, convertendo-os de volta em caracteres legíveis para descobrir a flag.

## Solution
Comecei convertendo cada caractere da string **label** em seus respectivos valores [ASCII](https://www.ime.usp.br/~kellyrb/mac2166_2015/tabela_ascii.html):
- **'l'** → 108
- **'a'** → 97
- **'b'** → 98
- **'e'** → 101
- **'l'** → 108
  
Depois, apliquei a operação **XOR** através de um [site](https://www.compscilib.com/calculate/binaryxor?variation=default) com o número **13** (representado como ^ 13):
-  108 ^ 13 = 97 → **'a'**
-  97 ^ 13 = 108 → **'l'**
-  98 ^ 13 = 111 → **'o'**
-  101 ^ 13 = 104 → **'h'**
-  108 ^ 13 = 97 → **'a'**

Resultado da transformação: **"aloha"**

## Flag
A conversão resultou na **flag**:
>`crypto{aloha}`

## Objetivo
Esse desafio foi uma forma simples de mostrar como uma operação básica, como o **XOR**, pode ser usada para esconder informações. Basta um número e uma operação para transformar completamente uma mensagem.
