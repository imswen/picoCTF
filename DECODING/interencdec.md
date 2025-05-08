# [interencdec]
###### Solved by @[imswen]
> This is a CTF about [Decoding]
## About the Challenge
Ao acessar o desafio, somos apresentados à seguinte mensagem de introdução:
>Can you get the real meaning from this file.

- [Página do Desafio](https://play.picoctf.org/practice/challenge/418)
  
Além disso, é fornecido um [link de download]([http://verbal-sleep.picoctf.net:56571](https://artifacts.picoctf.net/c_titan/108/enc_flag)), sugerindo que a resolução do desafio envolve analisar e decodificar o conteúdo desse arquivo.

## Solution
Após baixar o arquivo, tentei abri-lo com um editor de texto simples, como o **Bloco de Notas**. Dentro, encontrei o seguinte conteúdo:
>YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyZzBOMm8yYXpZNWZRPT0nCg==

Esse texto é uma string típica em **Base64**, é fácil de identificar pelo uso exclusivo de letras maiúsculas/minúsculas, números, +, / e =, e o final com ==. Então usei um decodificador online de Base64 e obtive o seguinte resultado:
>d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2g0N2o2azY5fQ

Ainda parecia ser uma string codificada em Base64, então realizei uma segunda decodificação. O segundo resultado foi:
>wpjvJAM{jhlzhy_k3jy9wa3k_h47j6k69}

Decidi jogar o texto diretamente no [dCode](https://www.dcode.fr/en), uma ferramenta bastante útil para identificar esse tipo de criptografia. O próprio dCode identificou que se tratava de uma **Cifra de César**. A decodificação resultou na flag:
>`[picoCTF{caesar_d3cr9pt3d_a47c6d69}]`
 
