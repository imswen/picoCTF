# [Cookie Monster Secret Recipe - picoCTF 2025]
###### Solved by @[imswen]
> This is a CTF about [Web Exploration]
## About the Challenge
Ao acessar o desafio, nos deparamos com a seguinte mensagem de introdução:
>Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe?

- [Página do Desafio](https://play.picoctf.org/practice/challenge/469)

Além disso, é fornecido um [link](http://verbal-sleep.picoctf.net:56571) indicando que o objetivo do desafio está ligado diretamente à interação com esse site.


Essa descrição sugere que a flag está escondida em algum lugar no site, incentivando o usuário a investigá-lo a fundo.
## Solution
Inicialmente, tentei realizar o login utilizando diferentes combinações de nome de usuário e senha. Percebi, no entanto, que qualquer entrada levava a uma página informando que o Cookie Monster não utiliza senhas, mas sim cookies. Como o enunciado do desafio enfatizava repetidamente a ideia de "cookie", resolvi investigar os cookies armazenados pelo site.

Utilizando as ferramentas de desenvolvedor do navegador, acessei a aba de "Aplicação" (Application), onde ficam salvos os cookies gerados durante a navegação. Lá, identifiquei um valor suspeito: uma string aparentemente codificada em Base64. 

![Imagem1.png](https://i.imgur.com/T2hScWP.png)

Após decodificá-la, obtive a flag do desafio:
>`[picoCTF{c00k1e_m0nster_l0ves_c00kies_96F58DAB}]`

Essa análise mostra como o desafio estava centrado no entendimento e inspeção de cookies HTTP, comum em contextos de segurança e CTFs (Capture the Flag).
