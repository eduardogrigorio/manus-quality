<div align="center">

```
 __  __    _    _   _ _   _ ____     ___  _   _  _    _     ___ _______   __
|  \/  |  / \  | \ | | | | / ___|   / _ \| | | |/ \  | |   |_ _|_   _\ \ / /
| |\/| | / _ \ |  \| | | | \___ \  | | | | | | / _ \ | |    | |  | |  \ V /
| |  | |/ ___ \| |\  | |_| |___) | | |_| | |_| / ___ \| |___ | |  | |   | |
|_|  |_/_/   \_\_| \_|\___/|____/   \__\_\\___/_/   \_\_____|___| |_|   |_|
```

### ⚡ Menos tokens. Mais acerto. Créditos intactos. ⚡

![Agent Skills](https://img.shields.io/badge/Agent%20Skills-compat%C3%ADvel-7c3aed?style=for-the-badge)
![Tamanho](https://img.shields.io/badge/SKILL.md-enxuto-22c55e?style=for-the-badge)
![Enrolação](https://img.shields.io/badge/enrola%C3%A7%C3%A3o-0%25-ef4444?style=for-the-badge)
![Loops](https://img.shields.io/badge/loops-max%202%20tentativas-f59e0b?style=for-the-badge)

*Uma skill para agentes como o **Manus** pararem de enrolar e começarem a entregar.*

</div>

---

## 🧠 O problema

Agente de IA cobra por **passo**, **ferramenta** e **texto**. E tem agente que:

- 🗣️ abre com "Ótima pergunta!" e repete o que você acabou de pedir
- 🔁 faz 5 buscas quase idênticas
- 📝 regera o arquivo inteiro para mudar uma linha
- 🌀 entra em loop tentando a mesma coisa que já falhou
- 🎁 entrega extras que ninguém pediu

Resultado: crédito queimado e resposta que poderia caber em 3 linhas.

## 🚀 A solução

`manus-quality` aplica uma regra simples: **esforço proporcional ao pedido**.

```
pedido ──► classifica ──► executa no nível certo ──► verifica o necessário ──► entrega
              │
              ├─ 🟢 Simples   → responde direto
              ├─ 🟡 Média     → plano curto + conferência
              └─ 🔴 Complexa  → trabalho completo, com fontes e testes
```

| Nível | Exemplos | O que o agente faz |
|---|---|---|
| 🟢 **Simples** | pergunta, fato, ajuste pequeno | Responde direto, até 1 busca, sem verificação extra |
| 🟡 **Média** | análise, documento, planilha, código pequeno | Plano curto, 3 a 8 chamadas de ferramenta, uma conferência final |
| 🔴 **Complexa** | entregável importante, pesquisa ampla, ação cara ou irreversível | Trabalho completo: fontes, testes, revisão |

> Na dúvida entre dois níveis, usa o menor e só sobe se o resultado exigir. 🎯

## 🧬 Regras do código-fonte (do comportamento)

| # | Regra | Em português claro |
|---|---|---|
| 1 | `answer_first()` | Começa pela resposta, sem abertura nem eco do pedido |
| 2 | `ask_once()` | Pergunta só se faltar algo crítico, tudo em uma mensagem |
| 3 | `search_smart()` | Uma busca boa vale mais que cinco parecidas |
| 4 | `edit_dont_regen()` | Muda o trecho, não o arquivo inteiro |
| 5 | `no_hallucination()` | Se não achou, diz "não encontrei". Nada de link ou citação inventada |
| 6 | `confirm_before_risk()` | Confirma antes de gastar muito, apagar, enviar ou publicar |
| 7 | `max_retries = 2` | Falhou duas vezes? Para, relata e propõe o caminho mais barato |
| 8 | `verify_proportionally()` | Confere de verdade quando importa, não repete conferência à toa |
| 9 | `close_short()` | No máximo 2 linhas no fim, e só se houver algo a avisar |

## 🎬 Antes e depois

**Pedido:** *"Qual a capital da Austrália e a população?"*

| ❌ Sem a skill | ✅ Com a skill |
|---|---|
| Parágrafos de contexto histórico, 3 buscas, lista de curiosidades e "posso ajudar com mais alguma coisa?" | **Canberra, cerca de 450 mil habitantes.** Uma busca, uma linha. |

## 📦 Instalação

**🤖 Manus**
1. Abra a área de **Skills**
2. Importe o arquivo `manus-quality.skill`
3. Substitua a versão anterior, se houver

**🧩 Claude e outros agentes compatíveis**
- Coloque a pasta `manus-quality/` no diretório de skills da ferramenta, **ou**
- Envie o `.skill` pela opção de upload de skills

## 🗂️ Estrutura

```
manus-quality/
└── SKILL.md      # o cérebro da operação
```

Um arquivo só. Sem dependências, sem scripts, sem drama. 🧘

## 🔧 Customize (modo hacker)

Abra o `SKILL.md` e mexa no que quiser:

- 🎛️ **`description`** no cabeçalho: define quando a skill dispara
- 📏 **Limites de esforço**: ajuste os números da seção "Classifique antes de agir"
- 🧪 **Regras novas**: adicione cuidados para o tipo de tarefa que mais falha (planilhas, slides, sites, pesquisa)

⚠️ **Dica de ouro:** mantenha o `SKILL.md` enxuto. Ele entra no contexto toda vez que a skill é usada, então inchar o arquivo também gasta crédito. Seria irônico, né?

## ⚖️ Limitações (a gente é honesto)

- A skill **orienta** o agente, mas não garante resultado. É instrução, não mágica. 🪄
- Se o agente ainda estiver prolixo, pegue exemplos reais de respostas longas demais e use-os para ajustar as regras.
- Não foi testada em todas as versões do Manus. Valide no seu fluxo antes de confiar em tarefas críticas.

---

<div align="center">

**Feito para quem quer que cada crédito conte.** 💎

`> ship it, don't ramble.`

</div>
