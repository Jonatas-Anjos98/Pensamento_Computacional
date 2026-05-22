# Aula_Organizacao_Dados_Grupo1

## Atividade: Do caos à organização – Estruturando Dados

Este repositório contém a resolução da atividade proposta na disciplina de Pensamento Computacional, que visa explorar diferentes formas de estruturar e representar um mesmo conjunto de dados utilizando estruturas computacionais fundamentais: Lista, Grafo e Hierarquia.

## Tema Escolhido

O tema central escolhido para esta atividade é **"Sistema de Compras de uma Loja Virtual"**, baseado no código Portugol fornecido. Este tema permite a representação das diversas etapas e componentes de um processo de compra online, desde a busca de produtos até a confirmação do pedido.

## Objetivos

1.  **Representar dados:** Demonstrar como um sistema complexo, como um processo de compra, pode ser modelado de diferentes maneiras para atender a distintas necessidades de análise e visualização.
2.  **Aplicar estruturas computacionais:** Utilizar corretamente as estruturas de Lista, Grafo e Hierarquia para organizar informações sobre as fases, módulos e interações do sistema de compras.
3.  **Desenvolver raciocínio computacional:** Reforçar a compreensão sobre a importância da escolha da estrutura de dados adequada para a eficiência e clareza na manipulação de informações e processos.

---

# Grafo

O grafo representa o fluxo lógico e as conexões entre as diferentes etapas do sistema de compras. Cada etapa é um vértice e as transições lógicas são as arestas.

## Principais Conexões:

- Início → Busca de Produto → Exibição de Resultados.
- Exibição de Resultados → Escolha do Produto → Validação.
- Validação (Sucesso) → Adição ao Carrinho → Atualização do Total.
- Carrinho → Loop de Adição (Sim) → Nova Busca.
- Carrinho → Finalizar Compra (Não) → Cálculo de Frete.
- Cálculo de Frete → Escolha de Opção → Pagamento.
- Pagamento → Escolha de Método (Cartão/Boleto/PIX) → Validação de Pagamento.
- Validação de Pagamento (Sucesso) → Geração de Pedido → Fim.

---

# Descrição da Hierarquia (Estrutura Lógica)

A hierarquia organiza os componentes do sistema por categorias funcionais, mostrando como o código está estruturado em termos de responsabilidades.

## Estrutura de Níveis:

- Sistema de Compras (Raiz)
- Inicialização
  - Declaração de Variáveis
- Fluxo Principal de Compra
  - Fase 1: Acesso e Busca
  - Fase 2: Escolha do Produto
  - Fase 3: Carrinho
  - Fase 4: Entrega e Frete
  - Fase 5: Pagamento
  - Fase 6: Confirmação Final
- Componentes de Validação
  - Validação de Escolha de Produto
  - Validação de Frete
  - Validação de Pagamento (Cartão)
- Componentes de Simulação
  - Simulação de Resultados de Busca
  - Simulação de Cálculo de Frete