## O router como "câmara" da casa

O router é quem **dá os IPs** e **encaminha o trânsito**, por isso, dentro de
casa, vê quem fala com quem, a que horas e em que portas. Um aparelho não se
consegue esconder do router dentro da rede.

> Analogia: o router é como uma câmara que vê tudo o que se passa dentro de casa.

### E a VPN?

A VPN cria um **túnel encriptado** para o trânsito que vai **para a internet**.
Com VPN, o router vê que o aparelho está a enviar dados e **quando**, mas **não
vê o conteúdo nem o destino final**.

Pontos importantes:

- Mesmo com VPN, o router continua a saber **qual** aparelho a usou e a que
  horas. A VPN esconde o **destino**, não esconde que o aparelho esteve ativo.
- O trânsito **interno** (de aparelho para aparelho na mesma rede) normalmente
  **não passa pela VPN** — é local. Por isso o router continua a ver "este
  aparelho falou com aquele, a esta hora".
- Numa Smart TV ou aparelho simples, pôr uma VPN é difícil ou impossível — por
  isso raramente se escondem.

## O que a cifra tapa (e o que não tapa)

> Podes esconder **o que** foi dito, mas não **que** falaram.

- **Conteúdo** (o "recheio") → hoje vai quase sempre **cifrado**, graças ao
  HTTPS. Mas não é o router que cifra — são os próprios aparelhos, de origem.
- **Metadados** (quem fala com quem, quando, com que frequência, quanto dados)
  → ficam **sempre à vista**, porque o endereço tem de ir visível para a
  mensagem chegar ao destino.

> Analogia do correio: a carta lá dentro pode ir num cofre, mas o endereço no
> envelope tem de estar à mostra, senão não há entrega.

### Quando o conteúdo fica à vista

- Trânsito antigo ou mal configurado (HTTP simples, sem o "S").
- Aparelhos baratos ou mal feitos de "casa inteligente" (câmaras, tomadas) que
  falam sem cifra.

É precisamente nessas exceções que o lado forense "encontra ouro".

## Sniffers e porque a cifra é obrigatória

Um **sniffer** (ex.: Wireshark) apanha tudo o que passa na rede. Se o conteúdo
fosse em texto limpo, qualquer pessoa na mesma rede leria palavras-passe e
mensagens — foi assim antigamente, e era um desastre. Por isso o mundo passou a
**cifrar por omissão**.

Mesmo com tudo cifrado, o sniffer continua a ler os **metadados** — e muitas
vezes o **padrão** conta a história quase toda. Ex.: uma TV a falar com um
servidor desconhecido **todas as noites à mesma hora** é suspeito, mesmo sem ler
o conteúdo.

## Duas formas de investigar

### 1. Captura ao vivo (Wireshark)

Espiar o trânsito em tempo real:

1. Abrir o Wireshark e escolher a placa de rede (ex.: Wi-Fi).
2. Aplicar um filtro para ver só um aparelho:
