# microservices-proto

## Estrutura
- Contém todos os arquivos .proto dos microsserviços (order, payment, shipping).
- Os stubs gerados para Go ficam em `microservices-proto/golang/<serviço>`.
- Os stubs para uso nos microsserviços são gerados via script.

## Como gerar os stubs

1. Dê permissão de execução ao script (Linux/Mac):
   ```sh
   chmod +x run.sh
   ```
2. Execute o script:
   ```sh
   ./run.sh
   ```
3. Os arquivos gerados ficarão em `microservices-proto/golang/`.

## Integração
- Os microsserviços Go importam os stubs gerados a partir desta pasta.
- Mantenha os protos atualizados para garantir compatibilidade entre os serviços.
# Repositório de Protobufs dos Microsserviços

Este repositório contém os arquivos `.proto` utilizados para comunicação gRPC entre os microsserviços Order, Payment e Shipping.

## Estrutura

- `order/order.proto` - Definição do serviço e mensagens do Order
- `payment/payment.proto` - Definição do serviço e mensagens do Payment
- `shipping/shipping.proto` - Definição do serviço e mensagens do Shipping
- `golang/` - Stubs gerados em Go para cada serviço
- `run.sh` - Script para gerar os stubs a partir dos protos

## Como gerar os stubs Go

1. Certifique-se de ter Docker instalado.
2. Gere os arquivos Go para todos os serviços:
   ```sh
   # Exemplo para Shipping
   docker run --rm -v %cd%:/defs namely/protoc-all -f shipping/shipping.proto -o golang -l go --go-source-relative
   # Repita para order/order.proto e payment/payment.proto
   ```
3. Os arquivos gerados estarão em `golang/<serviço>/`.

## Observações
- O campo `go_package` dos protos já está configurado para o caminho correto.
- O script `run.sh` pode ser adaptado para rodar via Docker, caso o protoc local esteja bloqueado.

---

Dúvidas? Consulte o README do repositório dos microsserviços para instruções de execução do sistema completo.