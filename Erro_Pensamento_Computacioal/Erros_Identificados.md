# 🔍 Erros Identificados no Projeto

A seguir estão listados os erros encontrados na versão original do código do sistema de compras, classificados por tipo (sintaxe, lógica ou execução). As correções foram aplicadas e justificadas no arquivo `Projeto_Corrigido.md`.

## 1. Erros de Sintaxe

| Erro | Localização | Descrição |
|------|-------------|------------|
| Declaração incorreta de variável | `cadeia produto_busca[100]` | A variável `produto_busca` foi declarada como um vetor de 100 posições, mas deveria ser uma cadeia simples para armazenar o nome do produto digitado pelo usuário. |
| Redeclaração de variável em laço `para` | `para (inteiro i = 0; i < 3; i++)` | A variável `i` já foi declarada no início do programa. Em muitas versões do Portugol, não é permitido redeclarar uma variável dentro do comando `para`. O correto é usar apenas `para (i = 0; i < 3; i++)`. |

## 2. Erros de Lógica

| Erro | Localização | Descrição |
|------|-------------|------------|
| Total da compra fixo | `total = 99.90` | O valor total foi definido como R$ 99,90 independentemente do produto escolhido. O correto é extrair o preço do produto selecionado a partir da lista de resultados. |
| Frete não adicionado ao total | Após escolha da opção de frete | O custo do frete (R$ 10,00 ou R$ 20,00) não é somado ao valor total da compra, resultando em um valor final incorreto. |
| Capacidade limitada do carrinho | `cadeia carrinho[1]` | O carrinho foi declarado com tamanho fixo 1, impossibilitando a adição de múltiplos produtos. O sistema não permite comprar mais de um item. |
| Preço do produto não extraído da string | `produto_escolhido = lista_resultados[j-1]` | A variável `produto_escolhido` armazena uma string contendo nome e preço (ex: "teclado - R$ 50,00"). Para calcular o total, seria necessário extrair apenas o valor numérico. |

## 3. Erros de Execução (Potenciais)

| Erro | Localização | Descrição |
|------|-------------|------------|
| Falta de validação de índices | `produto_escolhido = lista_resultados[j-1]` e `entrega = opcoes_frete[j-1]` | Se o usuário digitar um número fora do intervalo válido (ex: 4 para produtos ou 3 para frete), ocorrerá acesso inválido ao vetor, causando erro de execução (índice inexistente). |
| Entrada do usuário com acentuação | `leia(resposta)` e comparação `resposta == "nao"` | O usuário pode digitar "não" (com acento) ou "nao" (sem acento). O código apenas trata "nao", ignorando outras variações, o que pode levar a comportamento inesperado. |
| Dados de cartão sem validação | Leitura de `numero_cartao`, `validade`, `cvv` | O sistema não valida se os dados do cartão estão no formato correto ou se não estão vazios. Isso pode causar falhas no processamento de pagamento. |

## 📌 Observações

- Os erros de sintaxe foram corrigidos conforme indicado nos comentários do código.
- Os erros de lógica e execução exigem alterações estruturais para tornar o sistema funcional e robusto.
- A correção completa e as justificativas estão documentadas no arquivo `Projeto_Corrigido.md`.