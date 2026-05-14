# ✅ Projeto Corrigido – Sistema de Compras

Abaixo está a versão corrigida do programa, com todos os erros de sintaxe, lógica e execução tratados. As justificativas para cada alteração estão indicadas nos comentários do código.

```portugol
programa {

  funcao inicio() {
    // Declaração de variáveis
    cadeia produto_busca, produto_escolhido, resposta, cep, metodo
    cadeia lista_resultados[3]
    cadeia carrinho[10]            // Corrigido: carrinho com capacidade para 10 produtos
    inteiro num_itens_carrinho = 0 // Controle de quantos itens foram adicionados
    cadeia opcoes_frete[2]
    cadeia entrega
    logico pagamento_ok
    real total = 0.0               // Inicializado
    real frete_valor = 0.0
    inteiro numero_pedido, i, j
    cadeia numero_cartao, validade, cvv
    real preco_produto = 0.0

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
    
    // FASE 2: ESCOLHA DO PRODUTO COM VALIDAÇÃO
    inteiro opcao_valida = 0
    enquanto (opcao_valida == 0) {
      escreva("Resultados encontrados:\n")
      para (i = 0; i < 3; i++) {
        escreva((i + 1), " - ", lista_resultados[i], "\n")
      }
      escreva("Escolha o número do produto desejado (1 a 3): ")
      leia(j)
      
      se (j >= 1 e j <= 3) {
        produto_escolhido = lista_resultados[j - 1]
        opcao_valida = 1
      } senao {
        escreva("Opção inválida. Digite um número entre 1 e 3.\n")
      }
    }
    
    // Extrai o preço do produto a partir da string (formato "nome - R$ XX,XX")
    inteiro pos_dolar = posicao("R$", produto_escolhido)
    se (pos_dolar > 0) {
      cadeia preco_str = substring(produto_escolhido, pos_dolar + 2, compr(produto_escolhido))
      // Substitui vírgula por ponto para converter para real
      preco_str = substituir(preco_str, ",", ".")
      preco_produto = real(preco_str)
    } senao {
      preco_produto = 0.0
    }
    
    // FASE 3: CARRINHO (agora suporta múltiplos produtos)
    escreva("Adicionando ", produto_escolhido, " ao carrinho...\n")
    carrinho[num_itens_carrinho] = produto_escolhido
    num_itens_carrinho = num_itens_carrinho + 1
    total = total + preco_produto
    escreva("Produto adicionado!\n")
    
    // Permite adicionar mais produtos? (simplificado: pergunta se deseja continuar)
    cadeia continuar
    escreva("Deseja adicionar outro produto? (sim/nao): ")
    leia(continuar)
    enquanto (continuar == "sim" ou continuar == "sim") {  // aceita "sim" sem acento
      escreva("Digite o nome do próximo produto: ")
      leia(produto_busca)
      // Simulação de busca (apenas para demonstração)
      lista_resultados[2] = produto_busca + " - R$ 99,90"
      escreva("1 - ", lista_resultados[0], "\n")
      escreva("2 - ", lista_resultados[1], "\n")
      escreva("3 - ", lista_resultados[2], "\n")
      escreva("Escolha o número: ")
      leia(j)
      se (j >= 1 e j <= 3) {
        produto_escolhido = lista_resultados[j - 1]
        // Extrai preço novamente
        pos_dolar = posicao("R$", produto_escolhido)
        se (pos_dolar > 0) {
          cadeia preco_str = substring(produto_escolhido, pos_dolar + 2, compr(produto_escolhido))
          preco_str = substituir(preco_str, ",", ".")
          preco_produto = real(preco_str)
        } senao {
          preco_produto = 0.0
        }
        carrinho[num_itens_carrinho] = produto_escolhido
        num_itens_carrinho = num_itens_carrinho + 1
        total = total + preco_produto
        escreva("Produto adicionado!\n")
      } senao {
        escreva("Opção inválida.\n")
      }
      escreva("Deseja adicionar outro produto? (sim/nao): ")
      leia(continuar)
    }
    
    escreva("Deseja finalizar compra? (sim/nao): ")
    leia(resposta)
    // Aceita "não" com acento também
    se (resposta == "nao" ou resposta == "não") {
      escreva("Compra cancelada.\n")
    } senao {
    
      // FASE 4: ENTREGA E FRETE
      escreva("Conteúdo do carrinho:\n")
      para (i = 0; i < num_itens_carrinho; i++) {
        escreva(carrinho[i], "\n")
      }
      escreva("Total (sem frete): R$ ", total, "\n")
      escreva("Informe seu CEP: ")
      leia(cep)
      
      // Simular cálculo de frete
      opcoes_frete[0] = "PAC - R$ 10,00 (5 dias)"
      opcoes_frete[1] = "SEDEX - R$ 20,00 (2 dias)"
      inteiro opcao_frete_valida = 0
      enquanto (opcao_frete_valida == 0) {
        escreva("Opções de frete:\n")
        para (i = 0; i < 2; i++) {
          escreva((i + 1), " - ", opcoes_frete[i], "\n")
        }
        escreva("Escolha a opção de entrega (1 ou 2): ")
        leia(j)
        se (j == 1) {
          entrega = opcoes_frete[0]
          frete_valor = 10.0
          opcao_frete_valida = 1
        } senao se (j == 2) {
          entrega = opcoes_frete[1]
          frete_valor = 20.0
          opcao_frete_valida = 1
        } senao {
          escreva("Opção inválida. Tente novamente.\n")
        }
      }
      
      total = total + frete_valor
      escreva("Frete escolhido: ", entrega, "\n")
      escreva("Total com frete: R$ ", total, "\n")
      
      // FASE 5: PAGAMENTO COM REPETIÇÃO E VALIDAÇÃO
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
            // Validação simples: não pode estar vazio
            enquanto (numero_cartao == "") {
              escreva("Número do cartão não pode estar vazio. Digite novamente: ")
              leia(numero_cartao)
            }
            escreva("Validade (MM/AA): ")
            leia(validade)
            enquanto (validade == "") {
              escreva("Validade não pode estar vazia. Digite novamente: ")
              leia(validade)
            }
            escreva("CVV: ")
            leia(cvv)
            // Validação: CVV deve ser numérico e ter 3 dígitos (simplificado)
            enquanto (compr(cvv) != 3 ou nao(eh_numero(cvv))) {
              escreva("CVV inválido. Digite 3 dígitos: ")
              leia(cvv)
            }
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
      
      // FASE 6: CONFIRMAÇÃO FINAL
      numero_pedido = 123456
      escreva("\nPedido confirmado!\n")
      escreva("Número do pedido: ", numero_pedido, "\n")
      escreva("E-mail de confirmação enviado para o cliente.\n")
      escreva("Compra finalizada com sucesso.\n")
    }
  }
}