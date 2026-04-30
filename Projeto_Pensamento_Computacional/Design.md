# Design do Sistema – Plataforma Acadêmica Inteligente

## 1. Decomposição (detalhada)

| Módulo | Responsabilidades |
|--------|-------------------|
| Autenticação | Cadastro, login, logout, recuperação de senha, perfil de usuário (aluno, professor, coordenador). |
| Gestão de disciplinas e notas | CRUD de disciplinas, lançamento de notas, cálculo automático de médias, histórico escolar. |
| Recomendação inteligente | Análise de desempenho, sugestão de materiais (vídeos, artigos, exercícios), alertas de baixo rendimento. |
| Painel de relatórios | Relatórios de aprovação/reprovação por turma, relatório individual do aluno, exportação em PDF/CSV. |

## 2. Reconhecimento de Padrões

- **Login com dupla verificação** → inspirado no padrão de sistemas bancários e e-mail (autenticação em dois fatores).
- **Estrutura de notas** → similar a LMS como Moodle e Blackboard: média ponderada, possibilidade de recuperação, lançamento por bimestre/semestre.
- **Recomendações** → filtragem colaborativa (alunos com perfil de dificuldade semelhante buscaram os mesmos materiais complementares).
- **Relatórios** → padrão de geração assíncrona com fila de tarefas para não travar a interface do usuário.

## 3. Abstração (Diagrama de Classes)

Foram abstraídos detalhes de infraestrutura (banco de dados, rede, balanceamento de carga) para focar nas entidades centrais do domínio. O diagrama de classes abaixo mostra os relacionamentos essenciais.

**Classes principais:**
- `Usuario` → contém dados de login e tipo (aluno, professor, coordenador)
- `Disciplina` → representa as matérias ofertadas
- `Nota` → armazena avaliações de um usuário em uma disciplina
- `Recomendacao` → sugestões de conteúdo personalizadas
- `Relatorio` → documentos gerados sob demanda

*(Veja o diagrama completo no arquivo `diagrama.mmd`)*

## 4. Algoritmos

### Algoritmo 1 – Cálculo de Média Final

função calcular_media(notas):
    soma_ponderada = 0
    soma_pesos = 0
    para cada nota em notas:
        soma_ponderada += nota.valor * nota.peso
        soma_pesos += nota.peso
    media = soma_ponderada / soma_pesos

    se media >= 7:
        situacao = "Aprovado"
    senão se media >= 4:
        situacao = "Recuperação"
    senão:
        situacao = "Reprovado"

    retornar media, situacao

### Algoritmo 2 – Geração de Recomendações Personalizadas

função recomendar(usuario_id, disciplina_id):
    media = obter_media_final(usuario_id, disciplina_id)
    faltas = contar_faltas(usuario_id, disciplina_id)
    carga = obter_carga_horaria(disciplina_id)
    recomendacoes = []

    se media < 6:
        recomendacoes += buscar_materiais_por_disciplina(disciplina_id, nivel="iniciante")

    se faltas > (carga * 0.25):
        recomendacoes.adicionar("Plano de recuperação de faltas - procure a coordenação")

    perfis_similares = buscar_alunos_com_desempenho_similar(usuario_id, disciplina_id)
    para cada aluno em perfis_similares:
        materiais = buscar_materiais_utilizados(aluno.id, disciplina_id)
        recomendacoes.adicionar(materiais)

    retornar recomendacoes (limitado a 5 itens únicos)

