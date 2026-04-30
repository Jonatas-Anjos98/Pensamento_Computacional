# Projeto – Pensamento Computacional para Sistemas de Larga Escala

## Descrição

Este projeto foi desenvolvido como parte da disciplina **Pensamento Computacional** no curso de análise e desenvolvimento de sistemas, com a Profa. Kadidja Valéria.

O objetivo é aplicar os conceitos de pensamento computacional e engenharia de software na concepção de um sistema de larga escala, explorando **decomposição**, **abstração**, **reconhecimento de padrões** e **algoritmos**.

## Objetivos

- Relacionar engenharia de software e pensamento computacional.
- Reconhecer princípios e padrões relevantes para sistemas de larga escala.
- Identificar dificuldades reais no desenvolvimento de aplicações complexas.
- Aplicar metodologias ágeis no planejamento do projeto.

## Sistema Proposto

**Nome do Sistema:** Plataforma Acadêmica Inteligente

**Descrição:**  
Uma aplicação web para gestão acadêmica que integra:

- Cadastro e autenticação de usuários.
- Módulo de disciplinas e notas.
- Sistema de recomendações personalizadas (IA).
- Painel de relatórios para coordenação.

## Pensamento Computacional Aplicado

### Decomposição
O sistema foi dividido em quatro módulos principais:
- **Autenticação** – login, cadastro, recuperação de senha.
- **Gestão de disciplinas e notas** – lançamento, edição, exclusão, cálculo de médias.
- **Recomendação inteligente** – sugestões de materiais baseadas no desempenho.
- **Painel de relatórios** – geração de relatórios de turmas, professores e alunos.

### Reconhecimento de Padrões
- Login semelhante a sistemas bancários (validação em duas etapas, hash de senha).
- Estrutura de notas inspirada em LMS (Blackboard, Moodle): pesos, médias parciais e finais.
- Recomendações usando padrão colaborativo (similar a Netflix/Amazon).

### Abstração
- Diagrama UML simplificado (classes: `Usuario`, `Disciplina`, `Nota`, `Recomendacao`, `Relatorio`).
- Modelagem apenas das responsabilidades essenciais de cada componente, ignorando detalhes de infraestrutura.

### Algoritmos
- **Fluxo de cálculo de médias:**  
  `(nota1*peso1 + nota2*peso2 + ...) / peso_total` → situação (aprovado/reprovado/recuperação).
- **Fluxo de recomendações personalizadas:**  
  Se média < 6 → recomendar vídeos e exercícios complementares da disciplina;  
  Se faltas > 25% → recomendar planejamento de estudos;  
  Baseado em padrões de alunos com perfil semelhante.

## Metodologia de Desenvolvimento

- **Metodologia:** Scrum
- **Sprints:** 2 semanas
- **Ferramentas:** GitHub Projects, Issues, Kanban

## Desafios Identificados

- Escalabilidade para milhares de usuários simultâneos.
- Segurança de dados sensíveis (princípios de Saltzer & Schroeder).
- Integração com sistemas externos (bibliotecas digitais, APIs de conteúdo).

## Estrutura do Repositório

Projeto_Pensamento_Computacional/
├── README.md
├── Design.md
├── diagrama.mmd
├── Desafios.md
└── src/
    └── app.py