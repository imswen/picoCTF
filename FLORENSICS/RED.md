# [RED]
###### Solved by @[imswen]
> This is a CTF about [Forensics]
## About the Challenge
Ao acessar o desafio, somos recebidos com a seguinte introdução enigmática:
>RED, RED, RED, RED

- [Página do Desafio](https://play.picoctf.org/practice/challenge/460)
  
Junto a isso, há um [link de download](https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png) de uma imagem, o que sugere que a chave para resolver o desafio está embutida nela.
## Solution
Baixei e abri o arquivo **red.png**. Visualmente, era apenas um quadrado vermelho sólido:

![Imagem5.png](https://i.imgur.com/pMP2Yia.png)

Como não havia nada aparente, decidi abrir o arquivo em um editor de texto. Ao abrir havia um **poema** escondido nos dados da imagem:
>Crimson heart, vibrant and bold,
>
>Hearts flutter at your sight.
>
>Evenings glow softly red,
>
>Cherries burst with sweet life.
>
>Kisses linger with your warmth.
>
>Love deep as merlot.
>
>Scarlet leaves falling softly,
>
>Bold in every stroke.

Voltando ao site do desafio, encontrei a seguinte dica:
>Red?Ged?Bed?Aed?

Imediatamente associei isso ao modelo de cores **RGBA** (Red, Green, Blue, Alpha), o que sugeria que as informações escondidas poderiam estar embutidas em algum canal da imagem, comum em desafios forenses.

Sabendo disso, utilizei a ferramenta [zsteg](https://github.com/zed-0xff/zsteg), para encontrar mensagens ocultas em imagens PNG por meio de **esteganografia**. Ao rodar a ferramenta:
![Imagem6.png](https://i.imgur.com/INIrazy.png)

Consegui extrair um texto codificado em **Base64** do **canal vermelho**. Bastou copiar o texto e decodificá-lo com um conversor [Base64](https://www.base64decode.org) para revelar a flag:
>`[picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}]`
 
