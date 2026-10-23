# manus-quality

Skill para agentes de IA como o **Manus** que torna o trabalho mais **assertivo, objetivo e econômico em créditos**, sem perder qualidade quando a tarefa exige.

Segue o padrão [Agent Skills](https://agentskills.io): uma pasta com um arquivo `SKILL.md`.

## Para que serve

Agentes consomem crédito em passos, chamadas de ferramenta e texto. Esta skill reduz o que não agrega valor:

- respostas longas, com abertura, repetição do pedido e explicação do processo;
- buscas e leituras repetidas;
- arquivos regenerados do zero para mudar uma linha;
- loops de tentativa e erro;
- extras que ninguém pediu.

## Como funciona

**Esforço proporcional ao pedido.** O agente classifica a tarefa antes de agir:

| Nível | Exemplos | Comportamento |
|---|---|---|
| Simples | pergunta, fato, ajuste pequeno | Responde direto, no máximo 1 busca, sem verificação extra |
| Média | análise, documento, planilha, código pequeno | Plano curto, 3 a 8 chamadas de ferramenta, uma conferência final |
| Complexa ou de alto risco | entregável importante, pesquisa ampla, ação cara ou irreversível | Trabalho completo, com fontes, testes e revisão |

Na dúvida entre dois níveis, usa o menor e sobe só se o resultado exigir.

## Regras principais

- **Resposta curta:** começa pela resposta, sem enrolação, e o tamanho acompanha o da pergunta.
- **Perguntar pouco:** só quando falta algo que muda o resultado, tudo em uma mensagem.
- **Prudência:** confirma antes de ações caras ou irreversíveis, e nunca inventa fatos, links ou citações.
- **Anti-loop:** se uma abordagem falha duas vezes, para, relata o que tentou e propõe o caminho mais barato.
- **Verificação na medida certa:** confere o entregável de verdade quando importa e não repete conferências sem necessidade.
- **Fechamento:** no máximo 2 linhas com suposições e limitações reais, se houver.

## Instalação

**Manus:** importe o arquivo `manus-quality.skill` na área de Skills e substitua a versão anterior, se houver.

**Claude e outros agentes compatíveis:** coloque a pasta `manus-quality/` (com o `SKILL.md`) no diretório de skills da ferramenta, ou envie o `.skill` pela opção de upload de skills.

## Estrutura

```
manus-quality/
└── SKILL.md
```

## Personalização

Para ajustar o comportamento, edite o `SKILL.md`:

- **Disparo:** mude o campo `description` do cabeçalho. É ele que define quando a skill é acionada.
- **Limites de esforço:** altere os números da seção "Classifique antes de agir" (por exemplo, o máximo de buscas).
- **Tarefas específicas:** acrescente regras para o tipo de trabalho que mais falha (planilhas, apresentações, sites, pesquisa).

Mantenha o `SKILL.md` enxuto, pois ele entra no contexto sempre que a skill é usada e isso também consome crédito.

## Limitações

A skill orienta o comportamento do agente, mas não garante o resultado. Se o agente continuar prolixo, ajuste as regras com base em exemplos reais de respostas que você considerou longas demais.
