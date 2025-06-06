## YOU EITHER KNOW, XOR YOU DON'T
###### Solved by @imswen
> Este é um CTF sobre a decodificação XOR

## About the Challenge
O enunciado nos dá a seguinte mensagem:
> I've encrypted the flag with my secret key, you'll never be able to guess it.
> Remember the flag format and how it might help you in this challenge!

- [Página do desafio](https://cryptohack.org/courses/intro/xorkey1/)

Junto disso, recebemos uma string hexadecimal:
> 0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e26345115010

A dica essencial está em **lembrar do formato da flag**, normalmente algo como **crypto{...}**, e como isso pode ser usado para descobrir a chave de criptografia.

![image](https://github.com/user-attachments/assets/a44a6b0d-ec49-4bc8-8ea3-ad4b9b856466)

## Solution
A solução foi feita com a ferramenta **[CyberChef](https://gchq.github.io/CyberChef/)**, utilizando uma técnica comum de XOR **[known-plaintext attack](https://en.wikipedia.org/wiki/Known-plaintext_attack) (ataque com texto conhecido)**.
No CyberChef, adicionei as seguintes operações:
- **From Hex:** para transformar o conteúdo de hexadecimal para bytes.
- **XOR:** inseri como chave a string 'crypto{', em modo ASCII.

A saída foi:
> myXORke+y_QHOMe$~seG8bGURNDFWg)a|TM!an

Apesar de parte do conteúdo estar ilegível, é possível visualizar nitidamente o trecho:
> myXORkey

Mantendo a operação **From Hex**, e altere a chave da operação XOR para **myXORkey**. O resultado agora é:
> crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4ll}

![image](https://github.com/user-attachments/assets/fc139eef-c3c3-4824-b5c8-ecf152fe4c38)

## Flag
> `crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4lly`
