# O Desafio do cofre

**Um desafio interativo para vivenciar a Zona de Desenvolvimento Proximal de Vygotsky.**

O aluno precisa descobrir a senha de quatro algarismos de um cofre a partir de seis pistas. No caminho, experimenta na prática a diferença entre o que consegue fazer sozinho e o que consegue fazer com mediação. Essa diferença é o núcleo do conceito de ZDP.

Projeto desenvolvido juntamente com a psicóloga **Nicolly Motta**, como atividade do mestrado em Psicologia, para a aula sobre a perspectiva histórico-cultural de Vygotsky.

---

## Proposta pedagógica

A atividade faz parte de um plano de aula cujo objetivo é relacionar desenvolvimento humano, ensino e aprendizagem na perspectiva de Vygotsky. Ela atende ao objetivo específico de **distinguir nível de desenvolvimento real, nível de desenvolvimento potencial e Zona de Desenvolvimento Proximal** por meio da exploração orientada de um recurso digital.

O princípio é não oferecer toda a ajuda de uma vez. O desafio é organizado em três momentos:

1. **Cofre 1: tentativa e mediação.** O aluno pode tentar sozinho, mas o painel de Mediação fica em destaque, logo acima das pistas. As orientações chegam uma de cada vez, só quando solicitadas, e cada uma destaca a pista a que se refere. Depois da terceira orientação, é possível ver a solução explicada passo a passo.
2. **Cofre 2: nova tentativa independente (opcional).** Uma senha nova, sorteada a cada acesso, com o mesmo tipo de pista e **sem orientações**. Ele verifica se o raciocínio construído com ajuda passou a ser do aluno.
3. **Fechamento.** O aluno vê o próprio percurso nos três momentos e o resultado da turma. O gráfico dá destaque a quem resolveu **com orientação**, que é o foco da atividade.

> A ZDP não é simplesmente o momento em que a pessoa encontra dificuldade. É a distância entre o que ela realiza de forma independente e o que realiza com orientação ou em colaboração (VYGOTSKY, 2007).


---

## Funcionalidades

- Cofre animado: rodas de dígitos que giram e porta que se abre ao acertar. Funciona com mouse, teclado e roda do mouse.
- Mediação progressiva no cofre 1, com três orientações e solução explicada.
- Cofre 2 gerado aleatoriamente com as mesmas características do cofre 1:
  - seis pistas, cada uma com 1 ou 2 dígitos corretos;
  - pelo menos uma pista "1 correto, na posição certa";
  - **solução única**;
  - **todas as seis pistas necessárias** para chegar à resposta.
- Rascunho de dígitos no cofre 2, para o aluno marcar dígitos descartados e confirmados.
- Registro anônimo dos resultados numa planilha do Google.
- Gráfico da turma no final da atividade e um **painel para projetar** em sala (`?painel`), atualizado a cada 15 segundos.
- Layout responsivo, foco visível para navegação por teclado e respeito à preferência de movimento reduzido.

---

## Como funciona por dentro

```
Aluno no navegador  →  index.html (GitHub Pages)
                          │  ao concluir cada cofre, envia os dados
                          ▼
                     Google Apps Script  →  Google Planilhas (aba "Respostas")
                          │
                          └─ devolve o resumo da turma para o gráfico
```

- **`index.html`**: o site inteiro, com HTML, CSS, JavaScript e a foto embutidos. Não precisa de servidor.
- **`Codigo.gs`**: script colado na planilha e publicado como App da Web. Recebe os dados (`doPost`) e devolve o resumo para o gráfico (`doGet`).

O site funciona normalmente sem a planilha. Nesse caso, o gráfico mostra dados de exemplo com um aviso.

### Dados coletados

Nenhum dado pessoal é coletado. Cada aluno recebe um código de sessão aleatório e gera uma linha ao concluir o cofre 1 e outra se fizer o cofre 2.

| Coluna | Conteúdo |
|---|---|
| `data_hora` | Momento do registro |
| `sessao` | Código anônimo que liga as duas linhas de um mesmo aluno |
| `etapa` | `cofre1` ou `cofre2` |
| `resultado` | Cofre 1: `sozinho`, `com_orientacao` ou `viu_solucao`. Cofre 2: `resolveu` ou `desistiu` |
| `tentativas` | Número de tentativas válidas |
| `orientacoes` | Quantas orientações foram pedidas (0 a 3) |
| `tempo_seg` | Tempo gasto no cofre, em segundos |
| `senha` | Senha do cofre resolvido |

---

## Observação ética

Os dados são anônimos e servem apenas para discussão acadêmica.

---

## Referências

- ANASTASIOU, L. G. C.; ALVES, L. P. *Processos de ensinagem na universidade: pressupostos para as estratégias de trabalho em aula*. Joinville: UNIVILLE, 2004.
- VYGOTSKY, L. S. *A formação social da mente: o desenvolvimento dos processos psicológicos superiores*. 7. ed. São Paulo: Martins Fontes, 2007.
- VIGOTSKI, L. S. *A construção do pensamento e da linguagem*. São Paulo: Martins Fontes, 2001.
- VIGOTSKII, L. S. Aprendizagem e desenvolvimento intelectual na idade escolar. In: VIGOTSKII, L. S.; LURIA, A. R.; LEONTIEV, A. N. *Linguagem, desenvolvimento e aprendizagem*. 5. ed. São Paulo: Ícone, 1988.
