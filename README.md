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

## 🎁 Ainda não tem o Manus?

Crie sua conta pelo link de convite abaixo. A página do convite fala em créditos grátis para começar (confira as condições na própria página):

<div align="center">

### 👉 [**Crie sua conta no Manus**](https://manus.im/invitation/TT2BVEECWQLDM9?utm_source=invitation&utm_medium=social&utm_campaign=copy_link) 👈

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

## 📦 Passo a passo (para quem nunca fez isso)

Leva uns 5 minutos. Siga na ordem. 👇

### 1️⃣ Crie sua conta
Clique no link de convite lá em cima e faça o cadastro. Se já tem conta, pule para o passo 2.

### 2️⃣ Baixe a skill
Você precisa do arquivo **`manus-quality.skill`**. Salve em um lugar fácil de achar, como a Área de Trabalho. Não precisa abrir nem descompactar.

### 3️⃣ Importe no Manus
1. Entre no Manus
2. Procure a área de **Skills** (geralmente nas configurações ou no menu do seu perfil)
3. Escolha a opção de **importar / enviar** uma skill
4. Selecione o arquivo `manus-quality.skill`
5. Confirme e ative a skill

> 💡 Os nomes e a posição dos menus podem mudar com o tempo. Se não achar, procure por "Skills" ou pergunte ao próprio Manus onde importar uma skill.

### 4️⃣ Teste se funcionou
Abra uma conversa nova e mande um pedido simples:

```
Qual a capital da Austrália?
```

✅ **Funcionou se** a resposta vier curta e direta, sem abertura nem enrolação.
❌ **Não funcionou se** vier cheia de contexto e explicações. Confira se a skill está ativada e tente de novo em uma conversa nova.

### 🆘 Plano B (se a importação não funcionar)
1. Abra o arquivo `SKILL.md` (está dentro de `manus-quality/`)
2. Copie todo o texto
3. Cole no início de uma conversa com o Manus e diga: *"Siga estas instruções em todas as respostas desta conversa."*

Funciona, mas vale só para aquela conversa. Já a skill instalada vale para todas.

### 🧩 Outros agentes (Claude e compatíveis)
Coloque a pasta `manus-quality/` no diretório de skills da ferramenta, ou use a opção de upload de skills.

## ❓ Perguntas rápidas

**Preciso saber programar?** Não. É só importar o arquivo e usar normalmente.

**Vai deixar o Manus pior em tarefas difíceis?** Não. Em tarefas complexas ou de alto risco, ele faz o trabalho completo. A economia vem de cortar o que não serve.

**Posso desativar depois?** Sim. É só desligar ou remover a skill na mesma área onde importou.

**Quanto vou economizar?** Depende do seu uso. A skill reduz passos e texto desnecessários, mas não dá para prometer um número exato.

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
