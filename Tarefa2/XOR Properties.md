# XOR PROPERTIES
###### Solved by @imswen
> Este desafio de CTF explora as propriedades da operação XOR e como usá-las para reverter uma cadeia de criptografias.

## About the Challenge
Ao acessar o desafio, somos recebidos com a seguinte **introdução**:
> In the last challenge, you saw how XOR worked at the level of bits. In this one, we're going to cover the properties of the XOR operation and then use them to undo a chain of operations that have encrypted a flag. Gaining an intuition for how this works will help greatly when you come to attacking real cryptosystems later, especially in the block ciphers category.
> 
> There are four main properties we should consider when we solve challenges using the XOR operator

O enunciado nos relembra algumas propriedades importantes da operação **XOR**:
- **Comutativa:** A ⊕ B = B ⊕ A
- **Associativa:** A ⊕ (B ⊕ C) = (A ⊕ B) ⊕ C
- **Elemento neutro:** A ⊕ 0 = A
- **Auto-inverso:** A ⊕ A = 0

Essas propriedades nos permitem **reorganizar** e **simplificar** expressões **XOR** para “cancelar” elementos, o que é especialmente útil para descriptografar mensagens.

![image](https://github.com/user-attachments/assets/07bd8906-90a1-4b95-884d-aaafaffd6058)

## Solution
Nos foram fornecidos os seguintes valores:
> KEY1 =         a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313  
> KEY2 ^ KEY1 =  37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e  
> KEY2 ^ KEY3 =  c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1  
> FLAG ^ K1^K2^K3 = 04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf

Analisando, percebi que elas estão em Base Hexadecimal. Então com a ajuda do [XOR Calculator](https://xor.pw/#) comecei a aplicar as operações XOR:

- **Passo 1: Encontrar KEY2**

Sabemos que 'KEY2 ^ KEY1 = resultado', então para encontrar KEY2 basta fazer:
> KEY2 = (KEY2 ^ KEY1) ^ KEY1

Após a operação obtive:
> KEY2 = 911404e13f94884eabbec925851240a52fa381ddb79700dd6d0d


- **Passo 2: Encontrar KEY3**

Sabemos que 'KEY2 ^ KEY3 = resultado', então:
> KEY3 = (KEY2 ^ KEY3) ^ KEY2

Obtendo:
> KEY3 = 504053b757eafd3d709d6339b140e03d98b9fe62b84add0332cc


- **Passo 3: Encontrar a FLAG**

Temos a seguinte informação:
> FLAG ^ KEY1 ^ KEY2 ^ KEY3 = valor fornecido

Primeiro, fiz a operação 'KEY1 ^ KEY2', resultando em:
> 37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e

Após, realizei a operação '(KEY1 ^ KEY2) ^ KEY3', obtendo:
> 679ce12554e557ada0e38f2e52f126e54240b2576c83c4196cd2


Por fim, realizei a operação XOR de '(FLAG ^ KEY1 ^ KEY3 ^ KEY2)' com o resultado obtido na anterior. Resultando na XORed Output:
> 63727970746f7b7830725f69355f61737330633161743176337d

## Flag
Como a flag precisa estar no formato '**crypto{flag}**', resolvi converter o valor da flag em Hexadecimal para ASCII utilizando um [conversor online](https://www.rapidtables.com/convert/number/hex-to-ascii.html). O que me retornou a flag:
> `crypto{x0r_i5_ass0c1at1v3}`
