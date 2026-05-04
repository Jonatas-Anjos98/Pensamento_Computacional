# Algoritmo: Compra em Loja Virtual (Passo a Passo)

## Descrição
Este algoritmo representa, de forma genérica, o processo de compra de um produto em qualquer e-commerce. Os detalhes físicos e específicos foram removidos, restando apenas a lógica essencial.

## Passo a Passo

1. **Iniciar o algoritmo**

2. **Acessar o site da loja virtual**
   - Abrir navegador
   - Ir para o endereço da loja

3. **Buscar o produto desejado**
   - Ler o nome do produto digitado pelo usuário
   - Executar a busca no site
   - Exibir a lista de resultados

4. **Selecionar o produto**
   - Escolher um item da lista (normalmente o primeiro ou o escolhido pelo usuário)

5. **Adicionar o produto ao carrinho**
   - Executar a ação de adicionar
   - Exibir mensagem de confirmação

6. **Perguntar se o usuário deseja finalizar a compra**
   - Se a resposta for **não**, encerrar o algoritmo
   - Se for **sim**, continuar

7. **Obter o conteúdo atual do carrinho**

8. **Solicitar o CEP para cálculo do frete**
   - Ler o CEP informado
   - Calcular as opções de frete (com base no CEP e nos itens do carrinho)

9. **Apresentar as opções de entrega e aguardar a escolha do usuário**
   - Selecionar a modalidade de entrega desejada

10. **Iniciar o processo de pagamento (com repetição até sucesso)**
    - Enquanto o pagamento **não for aprovado**, fazer:
      1. Exibir as formas de pagamento disponíveis (cartão, boleto, PIX)
      2. Ler a escolha do usuário
      3. **Se for cartão**:
         - Ler os dados do cartão (número, validade, CVV)
         - Tentar processar o pagamento
      4. **Se for boleto**:
         - Gerar o boleto bancário
         - Considerar pagamento aprovado (boleto gerado)
      5. **Se for PIX**:
         - Gerar o QR Code ou chave PIX
         - Aguardar confirmação (simulada)
      6. **Se for opção inválida**:
         - Exibir mensagem de erro e repetir
      7. Se o pagamento falhar (cartão recusado, etc.):
         - Exibir mensagem de erro
         - Voltar ao início do loop (permitir nova tentativa)

11. **Após o pagamento ser aprovado, gerar um número de pedido único**

12. **Salvar os dados do pedido** (carrinho, entrega escolhida, método de pagamento, número do pedido)

13. **Exibir mensagem de confirmação para o usuário** com o número do pedido

14. **Enviar um e‑mail de confirmação** para o endereço cadastrado do usuário

15. **Finalizar o algoritmo**

## Observação
Este passo a passo corresponde ao **Nível 3 de abstração** (algoritmo genérico). Ele pode ser facilmente convertido para qualquer linguagem de programação ou para pseudocódigo com sintaxe mais formal.