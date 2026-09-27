# Analise de cabeçalho no Wireshark
Analisando um cabeçalho com o wireshark.

# Análise de Cabeçalho IPv4 com Wireshark

Neste estudo, utilizei o **Wireshark** para analisar um pacote IPv4 gerado a partir de um comando `ping` do computador para o gateway padrão do roteador.

**IP de origem:** `192.168.1.6`  
**IP de destino:** `192.168.1.1`

## Ferramenta utilizada

- Wireshark

## Análise do cabeçalho IPv4

### Version
**Valor:** `4`

O campo Version indica a versão do protocolo IP utilizada. Como o endereço analisado é IPv4, o valor é `4`.

### IHL (Internet Header Length)
**Valor:** `5 (20 bytes)`

O valor `5` representa 5 blocos de 32 bits.

`5 × 4 = 20 bytes`

Portanto, o cabeçalho IPv4 possui 20 bytes.

### DSCP/ECN
**Valor:** `CS0 / Not-ECT`

- **DSCP CS0:** o pacote não possui uma marcação específica para tratamento de QoS.
- **ECN Not-ECT:** o pacote não está utilizando o mecanismo de notificação explícita de congestionamento.

### Total Length
**Valor:** `60 bytes`

Representa o tamanho total do pacote IPv4, incluindo o cabeçalho e os dados.

- Cabeçalho IPv4: `20 bytes`
- Dados: `40 bytes`
- Total: `60 bytes`

### Identification
**Valor:** `0xd2b9 (53945)`

É um identificador atribuído ao pacote IPv4. Ele é especialmente utilizado quando ocorre fragmentação, permitindo identificar quais fragmentos pertencem ao mesmo pacote original.

`0xd2b9` está em hexadecimal e `53945` é o mesmo valor em decimal.

### Flags
**Valor:** `0x0`

O campo Flags possui informações relacionadas à fragmentação. Neste pacote, não há indicação de fragmentação.

### Fragment Offset
**Valor:** `0`

Indica a posição de um fragmento dentro do pacote original. Como este pacote não foi fragmentado, o valor é `0`.

### TTL (Time To Live)
**Valor:** `128`

O TTL representa o limite de saltos que o pacote pode realizar. A cada roteador atravessado, o valor é reduzido em 1. Quando chega a `0`, o pacote é descartado.

### Protocol
**Valor:** `1 (ICMP)`

Indica o protocolo transportado pelo IPv4. O valor `1` corresponde ao **ICMP**, utilizado pelo `ping`.

### Header Checksum
**Valor:** `0xe4af`

É utilizado para verificar a integridade do cabeçalho IPv4.

> Observação: o Wireshark apresentou `[validation disabled]`, portanto não é possível concluir apenas por essa informação que não existem erros no pacote.

### Source Address
**Valor:** `192.168.1.6`

É o endereço IP do computador que enviou o pacote.

### Destination Address
**Valor:** `192.168.1.1`

É o endereço IP do gateway padrão que recebeu o pacote.

## ICMP

O IPv4 está transportando uma mensagem **ICMP**, protocolo utilizado pelo `ping` para testar a comunicação entre dispositivos.

## O que aprendi

Com essa análise, pude relacionar os conceitos estudados sobre o cabeçalho IPv4 com um pacote real capturado no Wireshark, observando campos como:

- Version
- IHL
- DSCP/ECN
- Total Length
- Identification
- Flags
- Fragment Offset
- TTL
- Protocol
- Header Checksum
- Source Address
- Destination Address
