# Jogo da Velha — UNIFOR

Aplicação web do Jogo da Velha desenvolvida como atividade prática da disciplina de Engenharia de Software, seguindo rigorosamente a Especificação de Caso de Uso (CDU) fornecida pelo Prof. Bezerra.

---

## Integrantes do Grupo

| Nome | Matrícula |
|---|---|
| Allison de Oliveira Girão | 2612756 |
| Maria Rafaele Gomes de Araújo | 2618240 |

**Grupo:** Grupo3-2026  
**Disciplina:** GR-R-262-T193-83 — Requisitos e Modelagem de Sistemas  
**Instituição:** Universidade de Fortaleza (UNIFOR)

---

## Link da Aplicação (GitHub Pages)

**https://AllisonOliv.github.io/jogo-da-velha-unifor/**

---

## Como Executar Localmente

1. Clone o repositório:
   ```bash
   git clone https://github.com/AllisonOliv/jogo-da-velha-unifor.git
   ```
2. Abra o arquivo `index.html` diretamente no navegador.  
   Não é necessário servidor, instalação ou dependência externa.

---

## Estrutura do Repositório

```
jogo-da-velha-unifor/
├── docs/
│   └── cdu_JogarJogodavelha.md   ← Especificação de Caso de Uso (CDU)
├── src/
│   └── index.html                ← Aplicação completa (HTML + CSS + JS)
├── index.html                    ← Entrada do GitHub Pages
├── README.md                     ← Este arquivo
└── RELATORIO_PROMPTS.md          ← Relatório de uso de IA e auditoria
```

---

## Funcionalidades Implementadas

- Modos de jogo: **2 Jogadores (PVP)** e **Contra o Computador**
- Formatos: **Partida Única** e **Melhor de 3 (MD3)**
- Placar acumulado entre rodadas
- Linha de vitória animada sobre as 3 células vencedoras
- Animação de confetes na vitória
- Efeitos sonoros sintetizados via **Web Audio API** (sem arquivos externos)
- Identidade visual institucional da **UNIFOR** (`#003366`, `#0056b3`, `#d97706`, `#f4f6f9`)
- Arquivo único `index.html` — sem dependência de servidor back-end

---

## Tecnologias

- HTML5
- CSS3
- JavaScript (ES6+)
- Web Audio API (nativa do navegador)
- Canvas API (confetes)
