## FAVOURITE BYTE
###### Solved by @imswen
> Este é um CTF sobre a decodificação XOR

## About the Challenge
Ao acessar o desafio, somos apresentados à seguinte explicação:
> "I've hidden some data using XOR with a single byte, but that byte is a secret. Don't forget to decode from hex first."

Isso indica que a mensagem foi codificada com **XOR** usando um único byte como chave, e que o conteúdo está em **hexadecimal**.

Nos é fornecida a seguinte string hexadecimal:
> 73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d

O enunciado também reforça que devemos decodificar o conteúdo do hex primeiro, e depois tentar encontrar a chave do XOR, um único byte desconhecido.

![image](https://github.com/user-attachments/assets/3b55f019-a2dc-46ab-a96c-50923da26d9b)

## Solution
Para resolver, utilizei a ferramenta **[CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')XOR_Brute_Force(1,100,0,'Standard',false,true,false,'')&input=NzM2MjY5NjA2NDdmNmIyMDY4MjEyMDRmMjEyNTRmN2Q2OTRmNzYyNDY2MjA2NTYyMjEyNzIzNGY3MjY5Mjc3NTZk)**, uma das mais práticas para esse tipo de análise.
No **CyberChef**, adicionei os seguintes blocos:
- **From Hex:** para converter a string hexadecimal em texto ou bytes.
- **XOR Brute Force** para tentar todas as 256 combinações possíveis de XOR com um único byte.

Colei o texto fornecido (em hex) no painel central, e no painel de saída (direita) encontrei a flag:
> Key = 10: crypto{0x10_15_my_f4v0ur173_by7e}

![image](https://github.com/user-attachments/assets/edfeb829-6727-44aa-85cc-1ca5eb97b4f9)


## Flag
> `crypto{0x10_15_my_f4v0ur173_by7e}`
