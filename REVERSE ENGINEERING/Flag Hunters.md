# [Flag Hunters]
###### Solved by @[imswen]
> This is a CTF about [Reverse Engineering]
## About the Challenge
Ao acessar o desafio, nos deparamos com a seguinte mensagem introdutória:
>Lyrics jump from verses to the refrain kind of like a subroutine call. There's a hidden refrain this program doesn't print by default. Can you get it to print it? There might be something in it for you.

- [Página do Desafio](https://play.picoctf.org/practice/challenge/472)

Também é fornecido um [link para download](https://challenge-files.picoctf.net/c_verbal_sleep/064d0eba10978d362ad2517e0e6c7d68185078e0b2fca217f8bce134d3180cfc/lyric-reader.py) de um script Python chamado lyric-reader.py, que roda uma poesia interativa.

Além disso, o desafio fornece um comando para se conectar via Netcat:
>$ nc verbal-sleep.picoctf.net 51134

## Solution
Ao abrir o script **Python**, percebi que ele lê um arquivo chamado **flag.txt** logo no início, inserindo seu conteúdo no começo da variável **secret_intro**. Essa variável é depois usada no início da string **song_flag_hunters**, que contém toda a letra da poesia, ou seja, a flag está embutida nas primeiras linhas dessa letra, mas não é exibida por padrão.

Como o script tenta abrir um arquivo local, concluí que a flag só será revelada se o código for executado remotamente, o que pode ser feito utilizando o Netcat. Para isso, usei o terminal interativo do próprio site do PicoCTF.

Durante a execução da poesia, o script chega a uma linha que contém a palavra CROWD. Nessa hora, ele solicita que o usuário digite algo, e armazena essa entrada substituindo a linha atual em **song_lines[lip]**.

![Imagem2.png](https://i.imgur.com/8A8st8N.png)

O ponto crucial está no fato de que essa entrada é dividida por ponto e vírgula (;) e processada como se fossem comandos independentes. Isso abre espaço para uma espécie de "injeção de instrução".

Descobri que, ao digitar algo como:
>Hello ;RETURN 0

O script divide isso internamente como:
>['Crowd: Hello', 'RETURN 0']

A segunda parte (RETURN 0) bate com a seguinte regex do código:

![Imagem3.png](https://i.imgur.com/8vMlNaj.png)

Isso faz com que o script altere o ponteiro de execução (lip) para a linha 0, que é justamente o início da variável **secret_intro**, onde está a flag.

Resultado: ao injetar ;RETURN 0 como parte da entrada da plateia, o código "pula" para o início da música e imprime a flag escondida.

![Imagem4.png](https://i.imgur.com/Gp2yQr2.png)

>`[picoCTF{70637h3r_f0r3v3r_ac197d12}]`
 
