# Atividade: Controle de Acesso em Sala de Aula
**Disciplina:** Pensamento Computacional  
**Professor:** Kadidja Váleria  
**Aluno:** Jonatas Anjos Nogueira  
**Data:** 23 de abril de 2026  

## 1. O Desafio: Controle de Acesso
Este documento apresenta a solução algorítmica para o desafio de controle de acesso de alunos em uma sala de aula, conforme proposto na Avaliação Docente (A2) da disciplina de Pensamento Computacional da UDF.
O principal objetivo é desenvolver a habilidade de propor soluções de forma clara, lógica e sistemática, utilizando estruturas de controle fundamentais da programação.
O algoritmo foi projetado para gerenciar a entrada de alunos com base na seguinte lógica:
- **Verificação:** Conferir se o nome do aluno está presente em uma lista oficial previamente definida.
- **Condição positiva:** Caso o aluno esteja na lista, o acesso é permitido.
- **Condição negativa:** Caso o aluno não esteja na lista, o acesso é negado e uma mensagem de erro é exibida.
- **Repetição:** O processo é repetido para todos os alunos presentes na fila.

## 2. Formato e Estrutura do Algoritmo
O algoritmo foi desenvolvido em pseudocódigo, utilizando a sintaxe do Portugol Studio, e faz uso das principais estruturas de controle: decisão e repetição.

### 2.1 Estrutura Condicional: Se-Então-Senão
A estrutura **Se-Então-Senão** é utilizada para tomar a decisão de permitir ou negar o acesso do aluno.
```plaintext
SE (aluno_encontrado) ENTÃO
    ESCREVA("ACESSO PERMITIDO")
SENÃO
    ESCREVA("ERRO: ACESSO NEGADO")
FIM_SE
```

### 2.2 Estrutura de Repetição: Para
Para garantir que todos os alunos sejam analisados, o algoritmo utiliza uma estrutura de repetição do tipo **Para**. Esse laço percorre todos os alunos da fila, aplicando a verificação e a decisão para cada um deles. Além disso, um segundo laço de repetição é utilizado para percorrer a lista oficial e verificar se o nome informado está presente.
```plaintext
PARA cada aluno na fila FAÇA
    verificar se o nome está na lista oficial
    SE estiver ENTÃO permitir acesso
    SENÃO negar acesso
FIM_PARA
```

## 3. Implementação em Portugol Studio
```portugol
programa {
  funcao inicio()
	{
		cadeia listaOficial[5] = {"Jonatas Anjos", "Marcos Melo", "José Cauã", "Maria fernanda", "Samuel Coutinho"}
		cadeia nomeAluno
		inteiro totalAlunosFila
		logico encontrado
		escreva("--- Sistema de Controle de Acesso - Sala de Aula ---\n")
		escreva("Quantos alunos estão na fila para entrar? ")
		leia(totalAlunosFila)
		para (inteiro i = 1; i <= totalAlunosFila; i++)
		{
			escreva("\nVerificando aluno ", i, " de ", totalAlunosFila, ".\n")
			escreva("Digite o nome do aluno: ")
			leia(nomeAluno)
			encontrado = falso
			para (inteiro j = 0; j < 5; j++)
			{
				se (nomeAluno == listaOficial[j])
				{
					encontrado = verdadeiro
					pare
				}
			}
			se (encontrado)
			{
				escreva(">>> ACESSO PERMITIDO. Bem-vindo(a), ", nomeAluno, "!\n")
			}
			senao
			{
				escreva("!!! ERRO: ACESSO NEGADO. O nome '", nomeAluno, "' não consta na lista oficial.\n")
			}
		}
		escreva("\n--- Processo de verificação concluído ---\n")
	}
}
```

## 4. Considerações Finais
O algoritmo apresentado realiza o controle de acesso de forma eficiente, aplicando corretamente estruturas condicionais e de repetição. A solução demonstra o uso de decisões lógicas, laços de repetição e organização do fluxo do programa, sendo essencial para o desenvolvimento do pensamento computacional e resolução de problemas reais.