# Relatório de Prompting e Auditoria de IA

**Atividade:** Desenvolvimento Guiado por Requisitos (Spec-Driven Development)  
**Disciplina:** GR-R-262-T193-83 — Requisitos e Modelagem de Sistemas  
**Integrantes:** Allison de Oliveira Girão (2612756) · Maria Rafaele Gomes de Araújo (2618240)  
**Grupo:** Grupo3-2026

---

## 1. Ferramenta de IA Utilizada

| Campo | Detalhe |
|---|---|
| Ferramenta | **Claude Code (Anthropic)** |
| Modelo | claude-sonnet-4-6 |
| Interface | Extensão VS Code (Claude Code) |
| Data de uso | 18/08/2026 |

---

## 2. Prompts Enviados e Respostas Obtidas

### Prompt 1 — Geração inicial do jogo

> *"Preciso que você analise esse caso de uso, que é de um trabalho da faculdade e crie um jogo da velha de modo que tudo que está escrito nesse arquivo precisa ser feito minuciosamente sem que falte nada, e nem acrescente nada que não está pedido aí."*

**Ação da IA:** Leu o CDU completo e gerou o arquivo `index.html` único com HTML, CSS e JavaScript, implementando todos os fluxos (P1–P7, A1–A3, E1), os 11 elementos de interface (UI-01 a UI-11), as 8 variáveis de estado da Seção 18, os efeitos sonoros via Web Audio API e os confetes via Canvas API.

**Resultado:** Arquivo funcional gerado na primeira tentativa, sem omissões identificadas.

---

### Prompt 2 — Auditoria das cores (Tópico 10 / RNF)

> *"As paletas das cores e de fundo estão de acordo com o que foi pedido no CDU?"*

**Resposta da IA:** Confirmou que as quatro cores institucionais estavam aplicadas corretamente:
- `#003366` — título, fundo do tabuleiro, placar X
- `#0056b3` — subtítulo, hover do botão
- `#d97706` — placar O, linha de vitória, símbolo 'O'
- `#f4f6f9` — fundo da página (`body`)

**Correção necessária:** Nenhuma.

---

### Prompt 3 — Auditoria de áudio e portabilidade (RNF)

> *"Sintetização de Áudio (Zero Dependência de Arquivos) e Portabilidade — esses dois critérios foram atendidos?"*

**Resposta da IA:** Confirmou que:
- Todos os sons (X, O, vitória, empate) são gerados via `createOscillator()` e `createGain()` da Web Audio API nativa.
- Nenhum arquivo externo (`.mp3`, CDN, `<script src>`) é carregado.
- O jogo roda abrindo `index.html` diretamente no navegador, sem servidor.

**Correção necessária:** Nenhuma.

---

### Prompt 4 — Auditoria do Tópico 13 (Interface Visual)

> *"O tópico 13 do CDU foi todo atendido?"*

**Resposta da IA:** Verificou cada um dos 11 elementos (UI-01 a UI-11) e o wireframe Low-Fi (IV2), confirmando conformidade total: subtítulo em caixa alta com `text-transform: uppercase`, dropdowns com as opções e padrões corretos, placar nas cores corretas, contador de rodada no formato `Atual/Total`, linha de vitória com `opacity: 0` inicial, botão REINICIAR JOGO sempre habilitado.

**Correção necessária:** Nenhuma.

---

### Prompt 5 — Auditoria do Tópico 16 (Checklist de Validação)

> *"Verifique se o checklist do tópico 16 está de acordo."*

**Resposta da IA:** Separou os itens em dois grupos: os verificáveis no código (fluxos, RNF, pós-condições, interface visual coerente) e os de qualidade do documento CDU (já validados pelos autores). Todos os itens com reflexo em código estavam atendidos.

**Correção necessária:** Nenhuma.

---

### Prompt 6 — Auditoria do Tópico 19 (Critérios de Aceite)

> *"Verifique agora o tópico 19 para ver se está de acordo também com o que foi pedido."*

**Resposta da IA:** Verificou os 7 critérios de aceite (CA-01 a CA-07) individualmente, citando as linhas de código correspondentes a cada critério.

**Correção necessária:** Nenhuma.

---

## 3. Erros Cometidos pela IA em Relação ao CDU

Durante todo o processo de auditoria, **nenhum erro de conformidade com o CDU foi identificado** nas respostas e no código gerado pela IA. A implementação cobriu:

- Todos os passos do Fluxo Principal (P1–P7)
- Todos os Fluxos Alternativos (A1, A2, A3)
- O Fluxo de Exceção (E1), incluindo a regra de **não incrementar** o número da rodada em empate no MD3
- Os Requisitos Não Funcionais (paleta, Web Audio API, arquivo único)
- Os 11 elementos de interface definidos no Tópico 13
- As 8 variáveis de estado da Seção 18

A postura adotada foi a de **Auditor de Qualidade**: cada seção do CDU foi verificada explicitamente após a geração do código, confirmando a aderência antes de avançar para a próxima etapa.

---

## 4. Tabela de Autoavaliação dos Critérios de Aceite

| ID | Critério | Implementado? | Evidência no Código |
|---|---|:---:|---|
| **CA-01** | Paleta de cores UNIFOR (`#003366`, `#0056b3`) e subtítulo *"UNIVERSIDADE DE FORTALEZA"* | ✅ | `color: #003366` no `h1`; `color: #0056b3` na `.subtitle` com `text-transform: uppercase` |
| **CA-02** | Impossível sobrescrever célula com 'X' ou 'O' | ✅ | `if (options[index] !== '') return;` |
| **CA-03** | Tabuleiro bloqueia cliques após vitória ou empate | ✅ | `disableBoard()` seta `running = false` e `cell.disabled = true` |
| **CA-04** | Modo CPU executa jogada automática do 'O' após breve pausa | ✅ | `cpuMove()` com `setTimeout(..., 400)` |
| **CA-05** | MD3: zera tabuleiro entre rodadas, encerra com 2 vitórias ou após 3ª rodada | ✅ | `winsX >= 2 \|\| winsO >= 2` → campeão; `currentRound < 3` → próxima rodada |
| **CA-06** | Linha contínua sobre as 3 células vitoriosas + confetes | ✅ | `showWinLine()` com `getBoundingClientRect` + rotação; `launchConfetti()` com 160 partículas |
| **CA-07** | Efeitos sonoros sem arquivos `.mp3` externos | ✅ | 4 `createOscillator()` distintos via Web Audio API nativa |
