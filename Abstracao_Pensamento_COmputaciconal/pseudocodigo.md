programa {
  
  funcao inicio() {
    // Declaração de variáveis
    // ERRO CORRIGIDO: produto_busca deve ser uma cadeia simples, não um vetor de 100 posições
    cadeia produto_busca, produto_escolhido, resposta, cep, metodo
    cadeia lista_resultados[3]
    cadeia carrinho[1]
    cadeia opcoes_frete[2]
    cadeia entrega
    logico pagamento_ok
    real total
    inteiro numero_pedido, i, j
    cadeia numero_cartao, validade, cvv

    // FASE 1: ACESSO E BUSCA
    escreva("Abrindo navegador...\n")
    escreva("Acessando o site da loja virtual...\n")
    escreva("Digite o nome do produto: ")
    leia(produto_busca)
    escreva("Buscando por ", produto_busca, "...\n")
    
    // Simulação de lista de resultados
    lista_resultados[0] = "teclado - R$ 50,00"
    lista_resultados[1] = "mouse - R$ 75,00"
    lista_resultados[2] = produto_busca + " - R$ 99,90"
    
    escreva("Resultados encontrados:\n")
    // ERRO CORRIGIDO: Removido "inteiro" de dentro do para, pois 'i' já foi declarado acima
    para (i = 0; i < 3; i++) {
      escreva((i + 1), " - ", lista_resultados[i], "\n")
    }
    escreva("Escolha o número do produto desejado: ")
    leia(j)
    produto_escolhido = lista_resultados[j - 1]
    
    // FASE 2: CARRINHO
    escreva("Adicionando ", produto_escolhido, " ao carrinho...\n")
    carrinho[0] = produto_escolhido
    escreva("Produto adicionado!\n")
    escreva("Deseja finalizar compra? (sim/nao): ")
    leia(resposta)
    
    se (resposta == "nao") {
      escreva("Compra cancelada.\n")
    } senao {
    
      // FASE 3: ENTREGA E FRETE
      escreva("Conteúdo do carrinho:\n")
      escreva(carrinho[0], "\n")
      total = 99.90
      escreva("Total: R$ ", total, "\n")
      escreva("Informe seu CEP: ")
      leia(cep)
      
      // Simular cálculo de frete
      opcoes_frete[0] = "PAC - R$ 10,00 (5 dias)"
      opcoes_frete[1] = "SEDEX - R$ 20,00 (2 dias)"
      escreva("Opções de frete:\n")
      // ERRO CORRIGIDO: Removido "inteiro" de dentro do para
      para (i = 0; i < 2; i++) {
        escreva((i + 1), " - ", opcoes_frete[i], "\n")
      }
      escreva("Escolha a opção de entrega: ")
      leia(j)
      entrega = opcoes_frete[j - 1]
      
      // FASE 4: PAGAMENTO COM REPETIÇÃO
      pagamento_ok = falso
      enquanto (pagamento_ok == falso) {
        escreva("Formas de pagamento:\n")
        escreva("1 - Cartão de crédito\n")
        escreva("2 - Boleto bancário\n")
        escreva("3 - PIX\n")
        escreva("Digite a opção desejada: ")
        leia(metodo)
        
        escolha (metodo) {
          caso "1":
            escreva("Número do cartão: ")
            leia(numero_cartao)
            escreva("Validade: ")
            leia(validade)
            escreva("CVV: ")
            leia(cvv)
            escreva("Processando pagamento...\n")
            pagamento_ok = verdadeiro
            escreva("Pagamento aprovado!\n")
            pare
          caso "2":
            escreva("Gerando boleto bancário...\n")
            pagamento_ok = verdadeiro
            escreva("Boleto gerado com sucesso!\n")
            pare
          caso "3":
            escreva("Gerando QR Code PIX...\n")
            pagamento_ok = verdadeiro
            escreva("Pagamento via PIX confirmado!\n")
            pare
          caso contrario:
            escreva("Opção inválida. Tente novamente.\n")
            pagamento_ok = falso
        }
        
        se (pagamento_ok == falso) {
          escreva("Falha no pagamento. Tente novamente.\n")
        }
      }
      
      // FASE 5: CONFIRMAÇÃO FINAL
      numero_pedido = 123456
      escreva("\nPedido confirmado!\n")
      escreva("Número do pedido: ", numero_pedido, "\n")
      escreva("E-mail de confirmação enviado para o cliente.\n")
      escreva("Compra finalizada com sucesso.\n")
    }
  }
}
