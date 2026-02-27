# MEGAPROMPT — Redesign Visual das 17 Tabelas Comparativas do Guia RICD

**Data:** 26/02/2026
**Para:** Novo chat de execução
**Premissa absoluta:** O conteúdo factual das 17 tabelas já foi revisado e validado (`RELATORIO_REVISAO.md`). Este plano trata EXCLUSIVAMENTE do redesign visual/estrutural. NÃO alterar dados, artigos, números ou texto substantivo.

---

## 1. CARDS DE REFERÊNCIA — ANATOMIA COMPLETA

Os dois cards de referência (`CARDEXEMPLO.MD` e `flashcard_cpi_poderes.html`) definem o padrão de excelência visual. Abaixo, a decomposição de TODAS as dimensões de design extraídas deles.

### 1.1 CARDEXEMPLO.MD — "Prazos de Uso da Palavra no Plenário"

**Arquivo:** `CARDEXEMPLO.MD` (na verdade HTML, 512 linhas, 16KB)
**Tema:** Todos os prazos de uso da palavra no Plenário

#### Anatomia estrutural (de cima para baixo):

| Camada | Elemento | Função | CSS/Classes |
|--------|----------|--------|-------------|
| 1 | **Banner escuro** | Contexto temático + badges de artigos + badge "hot" | `.banner`, `.badge-arts`, `.badge-hot` |
| 2 | **Pergunta** | Framing cognitivo — "Quais são todos os prazos..." | `.question` — fundo branco, borda inferior, bold 1.08rem |
| 3 | **Section labels** | Separadores de fase com ícone + linha expansível | `.sec-label` — uppercase, tracking 0.13em, `::after` line |
| 4 | **Grid de mini-cards** | 2 colunas, cada item é um "pcard" colorido por fase | `.cards-grid` — grid 1fr 1fr, gap 10px |
| 5 | **Mini-card (pcard)** | Unidade atômica: ícone + nome + artigo + número GIGANTE + sub-rows | `.pcard` com variantes `.pc-exp`, `.pc-com`, `.pc-dis`, `.pc-vot`, `.pc-ord`, `.pc-misc` |
| 6 | **Número gigante** | O dado-chave em 1.6rem bold mono com unidade separada | `.time-num` (1.6rem, 800, mono) + `.time-unit` (0.72rem) + `.time-qual` |
| 7 | **Sub-rows** | Detalhes secundários com seta ▸ | `.sub-rows` > `.sub-row` com `::before { content:'▸' }` |
| 8 | **Tags inline** | Classificadores (urgência, líder, qualquer) | `.tag-urg`, `.tag-lid`, `.tag-any` |
| 9 | **Banner de destaque** | Regra transversal importante (urgência) | `.urg-banner` — gradiente rosa, ícone ⚡, borda colorida |
| 10 | **Armadilhas CEBRASPE** | Grid 3 colunas com ~~errado~~ vs **certo** | `.cebraspe` > `.trap-grid` > `.trap` com `.wrong` (line-through red) e `.right` (green bold) |
| 11 | **Lei Seca** | Rodapé com citações legais condensadas | `.lei-seca` — fundo bege, borda top, font pequena |

#### Princípios de design extraídos:

- **D1 — Hierarquia tipográfica radical:** Números-chave em 1.6rem mono bold, labels em 0.8rem, artigos em 0.62rem mono muted
- **D2 — Cor por fase/categoria:** Cada fase da sessão tem sua paleta (expediente=roxo, comunicações=âmbar, discussão=verde, votação=vermelho, ordem=azul)
- **D3 — Atomicidade:** Cada informação é um mini-card independente, não uma linha de tabela
- **D4 — Pergunta como âncora:** O card começa com uma pergunta de prova
- **D5 — Sub-rows com marcador visual:** Detalhes hierarquizados com ▸
- **D6 — Armadilhas explícitas:** Seção dedicada a erros comuns de banca
- **D7 — Lei seca como rodapé:** Citação compacta de todos os artigos relevantes

### 1.2 flashcard_cpi_poderes.html — "Poderes da CPI"

**Arquivo:** `flashcard_cpi_poderes.html` (311 linhas, 11KB)
**Tema:** O que a CPI pode e não pode fazer

#### Anatomia estrutural:

| Camada | Elemento | Função | CSS/Classes |
|--------|----------|--------|-------------|
| 1 | **Header** | Tag de assunto + classificação | `.header` com `.tag` |
| 2 | **Divider gradient** | Separador visual roxo gradiente | `.divider` — 3px gradient |
| 3 | **Pergunta** | Centralizada, bold 17px, com subtítulo menor | `.question` |
| 4 | **Banner explicativo** | Contextualização conceitual (reserva de jurisdição) | `.banner` — fundo lilás, texto roxo |
| 5 | **Dual-column layout** | PODE (verde) vs NÃO PODE (laranja/vermelho) | `.columns` grid 2 colunas, `.col-pode`, `.col-naopode` |
| 6 | **Títulos de coluna** | ✅ PODE / 🚫 NÃO PODE | `.col-title-pode`, `.col-title-naopode` — uppercase 800 |
| 7 | **Sub-labels** | Agrupamentos internos (Art. 36 RICD / Jurisprudência STF) | `.sub-label` — border-left 3px, uppercase |
| 8 | **Rows com ícone** | Cada poder é ícone + texto com bold nos termos-chave | `.row` > `.icon` + `<span>` |
| 9 | **Alert box** | Nuances CEBRASPE — armadilhas específicas | `.alert-box` — fundo amarelo, borda, ⚠️ |
| 10 | **Base legal** | Tags de referência normativa | `.base-legal` > `.refs` > `.ref-tag` — pills azuis |
| 11 | **Lei Seca** | Citação compacta com 📜 | `.lei-seca` — fundo amarelo claro, border-left dourada |

#### Princípios de design extraídos:

- **D8 — Dualidade visual PODE/NÃO PODE:** Contraste cromático forte para distinções binárias
- **D9 — Ícones semânticos por item:** Cada poder tem um ícone relevante (🏦 banco, 🔒 vedação, etc.)
- **D10 — Sub-labels como divisores internos:** Agrupam itens dentro de uma coluna
- **D11 — Alert box para nuances de prova:** Diferente das armadilhas (que são errado/certo), as nuances são explicativas
- **D12 — Base legal como seção dedicada:** Tags-pills com todos os fundamentos normativos
- **D13 — Responsividade:** Grid colapsa para 1 coluna em mobile

---

## 2. ESTADO ATUAL DAS 17 TABELAS — O QUE EXISTE

As 17 tabelas estão DENTRO do `guia_ricd.html` na seção "14B — Tabelas Comparativas", usando o sistema de CSS existente do guia. Elas compartilham:

### CSS existente no guia (já definido):
- **Container:** `border-radius:12px`, `box-shadow`, `border-collapse:separate`
- **Header:** Gradiente escuro `#1e293b→#334155`, texto claro, uppercase, tracking
- **Zebra:** Alternância `rgba(59,130,246,.03)` em linhas pares
- **Hover:** `rgba(59,130,246,.08)` no hover
- **Row classes:** `row-q` (quórum/âmbar), `row-v` (vedação/vermelho), `row-c` (competência/verde), `row-pen` (penalidade/roxo), `row-pr` (procedimento/teal), `row-p` (prazo/azul)
- **tnum:** Font mono 1.35rem bold em 6 cores (`tnum-q`, `tnum-p`, `tnum-v`, `tnum-c`, `tnum-pen`, `tnum-pr`)
- **ttag:** Pills inline em 7 variantes (`ttag-sim`, `ttag-nao`, `ttag-obr`, `ttag-ved`, `ttag-esp`, `ttag-info`, `ttag-warn`)
- **tsub/tsub2:** Sub-detalhes (11px) em cor quórum ou muted
- **Dark mode:** Todas as classes têm variantes `.dark`
- **Mobile:** `@media(max-width:768px)` transforma tabelas em card layout com `data-label`
- **Bordas de parágrafo:** `.bp`, `.bq`, `.bc`, `.bv`, `.bpen`, `.bpr`

### Classificação atual das tabelas:

| Tab | Tema | Linhas | Enriquecimento visual atual |
|-----|------|--------|----------------------------|
| 1 | Regimes de tramitação | 4 | ✅ Completo (row classes + tnum + ttag + tsub) |
| 2 | Votação | 3 | ✅ Completo |
| 3 | Quóruns | 10 | ✅ Completo (tsub na maioria simples) |
| 4 | Comissões | 4 | ✅ Completo (tsub na CPI) |
| 5 | Sessões | 6 | ✅ Completo (tsub na solene) |
| 6 | Penalidades CE | 5 | ✅ Completo |
| 7 | Proposições | 11 | ✅ Completo |
| 8 | Órgãos | 15 | ✅ Completo (tsub em Mesa) |
| 9 | Comissões detalhe | 16 | ✅ Completo (colspan em vedação/perda/turmas) |
| 10 | Requerimentos | 18 | ✅ Completo |
| 11 | Prazos | 25 | ✅ Completo |
| **12** | **Ordem de pauta** | **9** | ⚠️ Parcial — row classes + tnum + ttag aplicados, mas sem tsub, sem data-label, sem refinamento semântico |
| **13** | **Tramitação** | **7** | ⚠️ Parcial — idem |
| **14** | **Disciplinar** | **10** | ⚠️ Parcial — idem |
| **15** | **Sessões detalhe** | **11** | ⚠️ Parcial — idem |
| **16** | **Temporárias** | **10** | ⚠️ Parcial — idem |
| **17** | **Atuação parlamentar** | **12** | ⚠️ Parcial — idem |

---

## 3. GAP ANALYSIS — O QUE FALTA

Comparando as Tabelas 1-11 (completas) com as Tabelas 12-17 (parciais), e INSPIRANDO-SE nos cards de referência, as seguintes dimensões faltam:

### 3.1 Dimensões de PARIDADE com Tabelas 1-11:

| Dimensão | Tab 1-11 | Tab 12-17 | Gap |
|----------|----------|-----------|-----|
| `tsub` (sub-detalhe numérico) | ✅ Presente em tab 3, 4, 5, 8 | ❌ Ausente | Adicionar tsub onde há limites/sub-regras |
| `tsub2` (sub-detalhe textual) | ✅ Presente | ❌ Ausente | Adicionar onde há notas complementares |
| `colspan` para regras transversais | ✅ Tab 9 usa 3x | ❌ Ausente | Identificar e aplicar |
| `data-label` mobile | ❌ Ausente em TODAS | ❌ Ausente | Aplicar a TODAS as 17 tabelas |
| Consistência semântica de row classes | ✅ Rigorosa | ⚠️ Questionável em pontos | Revisar mapeamento |
| Hierarquia tnum (q vs p vs v) | ✅ Precisa | ⚠️ Inconsistente | Revisar critérios |
| Booleans com ttag-sim/ttag-nao | ✅ Consistente | ⚠️ "Sim"/"Não" bare misturados | Padronizar |

### 3.2 Dimensões INSPIRADAS nos cards de referência (NOVAS para o guia):

Estas são inspirações dos cards de referência que podem ser adaptadas ao sistema de tabelas do guia SEM quebrar o design existente:

| Dimensão inspirada | Origem | Adaptação para tabelas |
|-------------------|--------|----------------------|
| **Pergunta-âncora** | CARDEXEMPLO `.question` | Adicionar um `<p class="bq">` antes de cada tabela com uma pergunta de prova que a tabela responde |
| **Banner de regra transversal** | CARDEXEMPLO `.urg-banner` | Criar classe `.rule-banner` para notas que se aplicam a toda a tabela (ex: "Em urgência, todos os prazos são reduzidos") |
| **Armadilhas CEBRASPE** | CARDEXEMPLO `.cebraspe` > `.trap` | Criar seção `.traps-grid` após cada tabela com pegadinhas ~~errado~~ vs **certo** |
| **Lei Seca compacta** | Ambos `.lei-seca` | Adicionar rodapé `.lei-seca` com todos os artigos da tabela em formato compacto |
| **Alert box de nuances** | CPI `.alert-box` | Criar `.alert-box` para nuances sutis que a banca cobra |
| **Base legal com ref-tags** | CPI `.base-legal` > `.ref-tag` | Converter as referências de artigos em tags-pills clicáveis |

---

## 4. PLANO FASEADO DE EXECUÇÃO

### FASE 0 — CSS: Novas classes inspiradas nos cards (EXECUTAR PRIMEIRO)

**Objetivo:** Criar no `<style>` do `guia_ricd.html` as novas classes CSS necessárias, sem mexer em nenhuma tabela.

```css
/* ===== FASE 0: Classes inspiradas nos cards de referência ===== */

/* Pergunta-âncora antes da tabela */
.tab-question {
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--text);
  line-height: 1.4;
  padding: 14px 18px;
  margin: 12px 0 4px;
  background: var(--bg-card);
  border: 1.5px solid var(--border);
  border-radius: 10px;
  text-align: center;
}
.tab-question em { font-weight: 400; color: var(--text-muted); font-size: 0.9em; }

/* Banner de regra transversal */
.rule-banner {
  margin: 4px 0 12px;
  background: linear-gradient(90deg, var(--c-vedacao-bg), var(--c-quorum-bg));
  border: 1.5px solid var(--c-vedacao-border);
  border-radius: 10px;
  padding: 10px 14px;
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 0.85rem;
  color: var(--text);
  line-height: 1.5;
}
.rule-banner strong { color: var(--c-vedacao); }

/* Grid de armadilhas CEBRASPE */
.traps-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 8px;
  margin: 12px 0;
}
.trap-card {
  background: var(--bg-card);
  border: 1.5px solid var(--c-quorum-border);
  border-radius: 9px;
  padding: 10px 12px;
  font-size: 0.8rem;
  color: var(--text);
  line-height: 1.45;
}
.trap-card strong { color: var(--text); font-weight: 700; }
.trap-wrong { color: #cc2200; text-decoration: line-through; font-size: 0.78rem; }
.trap-right { color: #1a6a20; font-weight: 700; }

/* Alert box de nuances */
.alert-nuance {
  margin: 8px 0;
  background: var(--c-quorum-bg);
  border: 1.5px solid var(--c-quorum-border);
  border-radius: 10px;
  padding: 10px 14px;
  font-size: 0.82rem;
  color: var(--text);
  line-height: 1.55;
}
.alert-nuance strong { color: var(--c-quorum); }

/* Base legal com ref-tags */
.base-legal-row {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin: 8px 0;
  padding: 8px 12px;
  background: var(--c-prazo-bg);
  border-radius: 8px;
}
.ref-tag {
  background: var(--c-prazo-border);
  color: var(--c-prazo);
  font-size: 0.68rem;
  font-weight: 600;
  border-radius: 6px;
  padding: 3px 8px;
  font-family: 'DM Mono', ui-monospace, monospace;
}

/* Lei Seca compacta */
.lei-seca-row {
  background: #f5f5ea;
  border-top: 1.5px solid #e0e0c0;
  border-radius: 0 0 12px 12px;
  padding: 8px 14px;
  font-size: 0.72rem;
  color: #5a5a30;
  line-height: 1.5;
  margin-top: -1px;
}
.lei-seca-row strong { color: #3a3a10; }

/* Dark mode para novas classes */
.dark .tab-question { background: var(--bg-card); border-color: var(--border); }
.dark .rule-banner { background: linear-gradient(90deg, rgba(239,68,68,.08), rgba(245,158,11,.08)); border-color: var(--c-vedacao); }
.dark .trap-card { border-color: var(--c-quorum); background: var(--bg-card); }
.dark .trap-wrong { color: #f87171; }
.dark .trap-right { color: #86efac; }
.dark .alert-nuance { background: rgba(245,158,11,.08); border-color: var(--c-quorum); }
.dark .base-legal-row { background: rgba(59,130,246,.08); }
.dark .ref-tag { background: rgba(59,130,246,.2); color: var(--c-prazo); }
.dark .lei-seca-row { background: rgba(245,245,234,.05); border-color: var(--border); color: var(--text-muted); }
.dark .lei-seca-row strong { color: var(--text); }

/* Mobile para traps-grid */
@media(max-width:768px){
  .traps-grid { grid-template-columns: 1fr; }
}
```

**Validação Fase 0:** Abrir o guia e confirmar que nenhuma renderização quebrou.

---

### FASE 1 — data-label mobile em TODAS as 17 tabelas

**Objetivo:** Adicionar `data-label="<header>"` a CADA `<td>` de CADA tabela para que o layout mobile funcione.

**Método:** Para cada tabela, ler os `<th>` do header e adicionar `data-label="Nome da Coluna"` a cada `<td>` correspondente.

**Exemplo (Tabela 1 — 4 linhas × 5 colunas = 20 tds):**
```html
<!-- ANTES -->
<td>Ordinária</td>

<!-- DEPOIS -->
<td data-label="Regime">Ordinária</td>
```

**Escopo:** 17 tabelas × média 8 linhas × média 5 colunas = ~680 `<td>` a atualizar.

**IMPORTANTE:** Fazer tabela por tabela, NÃO em batch. Ler a tabela, identificar os headers, aplicar data-labels.

**Ordem de execução:** Tabelas 1→17 sequencialmente.

---

### FASE 2 — tsub/tsub2 nas Tabelas 12-17

**Objetivo:** Adicionar sub-detalhes hierárquicos onde há números com contexto adicional, seguindo o padrão das Tab 1-11.

**Mapeamento específico por tabela:**

#### Tabela 12 (Ordem de pauta):
- Linha 1 (Redações finais): tsub "Parte integrante do turno" → mover para tsub2 dentro da célula Categoria
- Linha 5 (Urgência): tsub "guerra → defesa → urgente → acordos → FA" como hierarquia visual

#### Tabela 13 (Tramitação):
- PEC: tsub abaixo do quórum "308 Dep." → `<span class="tsub">em cada turno, nominal</span>`
- PEC: tsub em turnos → `<span class="tsub">interstício: 5 sessões</span>`
- PLP: tsub → `<span class="tsub">Também chamado PLC</span>`
- PL: tsub → `<span class="tsub">8 exceções à conclusividade</span>`

#### Tabela 14 (Disciplinar):
- Perda de mandato: tsub → `<span class="tsub">Prazo-limite: 90 dias úteis (Art. 16 CE)</span>`
- Suspensão: tsub → `<span class="tsub">Prazo-limite: 60 dias úteis (Art. 16 CE)</span>`

#### Tabela 15 (Sessões detalhe):
- Deliberativa Ordinária / Duração: tsub com breakdown "PE 60 + GE 50 + OD + CP"
- Comissão Geral: tsub → `<span class="tsub">1/3 = 171 ou Líderes</span>`

#### Tabela 16 (Temporárias):
- CPI / Prazo: tsub → `<span class="tsub">Máx. 5 simultâneas (Art. 35, §4º)</span>` (igual ao padrão da Tab 4)
- CPI / Prorrogação: tsub → `<span class="tsub">Total máx. 180 dias</span>`

#### Tabela 17 (Atuação parlamentar):
- Orientação de bancada: tsub → `<span class="tsub">Não vincula voto individual</span>`
- Parecer: tsub → `<span class="tsub">Empate = prevalece Relator</span>`

---

### FASE 3 — Refinamento semântico de row classes e tnum (Tabelas 12-17)

**Objetivo:** Garantir que cada row class e cor de tnum segue a mesma lógica semântica das Tab 1-11.

**Regras de mapeamento (extraídas das tabelas referência):**

| Classe | Semântica correta | Cor da borda |
|--------|-------------------|-------------|
| `row-q` | Linha cujo TEMA PRINCIPAL é um quórum, threshold ou limite numérico de deliberação | Âmbar |
| `row-v` | Vedação, exceção, restrição, proibição | Vermelho |
| `row-c` | Competência, atribuição, composição de órgão | Verde |
| `row-pen` | Penalidade, sanção, disciplina | Roxo |
| `row-pr` | Procedimento, prazo, trâmite, fluxo processual | Teal |
| `row-p` | Prazo temporal (raramente usado — geralmente absorvido por row-pr) | Azul |

| Classe tnum | Semântica correta |
|-------------|-------------------|
| `tnum-q` | Número de quórum (257, 308, 171, 51...) ou threshold |
| `tnum-p` | Prazo, duração, horário, período |
| `tnum-v` | Limite restritivo, máximo, mínimo, vedação numérica |
| `tnum-c` | Número de composição |
| `tnum-pen` | Número associado a penalidade |
| `tnum-pr` | Número de procedimento |

**Revisões específicas a fazer:**

#### Tabela 12:
- Ordinais (1º, 2º...) → **REMOVER tnum dos ordinais**. Na Tab 12 original, os ordinais são só indicadores de ordem, não dados numéricos de quórum/prazo. Manter texto normal.
- Usar tnum apenas em números substantivos (5 min do encaminhamento, 257 Dep.)

#### Tabela 14:
- `row-q` nas suspensões → corrigir para `row-pen` (são PENALIDADES, não quóruns)
- `row-pr` nas censuras → corrigir para `row-pen` (idem)

#### Tabela 15:
- Horários (14h, 9h, 16h) → remover tnum. Horários de sessão NÃO são prazos regimentais.
- Manter tnum apenas em: 60min, 50min, 5h, 4h, 30min, 1h (durações), 51, 257, 171 (quóruns)

#### Tabela 17:
- `row-v` em orientação/encaminhamento/destaque → corrigir para `row-pr` (são PROCEDIMENTOS de votação, não vedações)
- `row-q` em questão de ordem/reclamação → corrigir para `row-pr` (são procedimentos, o quórum é secundário)

---

### FASE 4 — Booleans padronizados com ttag-sim/ttag-nao (Tab 13)

**Objetivo:** Na Tabela 13, toda célula que responde "Sim" ou "Não" a uma pergunta (Apreciação conclusiva? / Revisão pelo Senado? / Comissão Especial?) deve usar ttag consistente.

**Regra:**
- "Sim" bare → `<span class="ttag ttag-sim">SIM</span>`
- "Não" bare → `<span class="ttag ttag-nao">NÃO</span>`
- "Sim (com qualificação)" → `<span class="ttag ttag-sim">SIM</span> (qualificação)`
- "Não (com qualificação)" → `<span class="ttag ttag-nao">NÃO</span> (qualificação)`

**Escopo:** ~15 células na Tabela 13 + verificar Tabelas 14-17 para padrão.

---

### FASE 5 — colspan para regras transversais (Tab 14, 15, 16)

**Objetivo:** Quando uma regra se aplica uniformemente a todas as colunas de uma tabela comparativa, usar colspan em vez de repetir.

**Candidatos identificados:**

#### Tabela 14 (Disciplinar):
- Adicionar linha colspan: "EC 76/2013 tornou OSTENSIVA a votação sobre perda de mandato nos incisos I, II e VI do Art. 55 CF" → Já está no `<p class="inc">`, mas merece destaque como `.rule-banner`

#### Tabela 16 (Temporárias):
- "Extinção" tem o mesmo padrão para as 3 comissões ("término da legislatura ou conclusão") → Candidato a colspan

---

### FASE 6 — Elementos inspirados nos cards de referência

**Objetivo:** Adicionar as dimensões NOVAS extraídas dos cards de referência.

#### 6A — Perguntas-âncora (`tab-question`)

Adicionar ANTES de cada tabela um `<p class="tab-question">` com uma pergunta de concurso que a tabela responde.

| Tabela | Pergunta-âncora |
|--------|----------------|
| 1 | Quais são os regimes de tramitação e suas consequências para inclusão na pauta? |
| 2 | Quais são as modalidades de votação e quando se usa cada uma? |
| 3 | Quais quóruns numéricos o RICD e o CE exigem e para que servem? |
| 4 | Quais são as espécies de comissões e como são criadas? |
| 5 | Quais são os tipos de sessão da Câmara e suas características? |
| 6 | Quais são as penalidades do Código de Ética e quem as aplica? |
| 7 | Quais são as espécies de proposição e seus quóruns de aprovação? |
| 8 | Quais são os órgãos da Câmara, sua composição e competências? |
| 9 | Como funcionam as Comissões — composição, quóruns e prazos? |
| 10 | Quais são os tipos de requerimento e seus quóruns? |
| 11 | Quais são os prazos regimentais para recursos, emendas e outros atos? |
| 12 | Em que ordem as matérias são apreciadas na Ordem do Dia? |
| 13 | Como tramitam as principais espécies de proposição? |
| 14 | Quais são as hipóteses de perda de mandato e os procedimentos disciplinares? |
| 15 | Quais são os parâmetros operacionais de cada tipo de sessão? |
| 16 | Como se comparam as três espécies de comissões temporárias? |
| 17 | Quais instrumentos de atuação o Deputado tem no Plenário e nas Comissões? |

#### 6B — Armadilhas CEBRASPE (`traps-grid`)

Adicionar após tabelas selecionadas (as que têm mais pegadinhas):

**Tabela 3 (Quóruns):**
```
⚠️ "1/10 para abertura = 52"? ERRADO. Na abertura de sessão, "desprezada a fração" = 51 (Art. 79, §2º). Mas 1/10 para recurso = 52 (arredondado para cima).
⚠️ "Maioria simples = metade + 1 dos membros"? ERRADO. É maioria dos PRESENTES, não dos membros.
```

**Tabela 13 (Tramitação):**
```
⚠️ "PL sempre vai ao Plenário"? ERRADO. PL pode ter apreciação conclusiva em Comissão (Art. 24, II).
⚠️ "PEC tem turno único"? ERRADO. PEC exige 2 turnos com interstício de 5 sessões.
```

**Tabela 14 (Disciplinar):**
```
⚠️ "Perda de mandato é por voto secreto"? ERRADO desde EC 76/2013. Votação OSTENSIVA para incisos I, II e VI.
⚠️ "Mesa DECIDE sobre perda de mandato"? ERRADO. Mesa DECLARA apenas nos incisos III-V. Nos demais, o Plenário DECIDE.
```

#### 6C — Lei Seca compacta (`lei-seca-row`)

Adicionar após cada tabela um rodapé com todos os artigos citados em formato condensado. **Aplicar a TODAS as 17 tabelas.**

Exemplo para Tabela 12:
```html
<div class="lei-seca-row">
  <strong>📜 Lei Seca:</strong> Art. 83, I–V e par.ún. · Art. 159, §§1º–3º · Art. 160, §4º · Art. 167 · Art. 195, §1º · Art. 154, §1º.
</div>
```

#### 6D — Alert box de nuances (`alert-nuance`)

Adicionar antes de tabelas selecionadas que têm distinções sutis:

**Tabela 14:**
```html
<div class="alert-nuance">
  ⚠️ <strong>Nuance crucial:</strong> Há dois regimes de perda de mandato — nos incisos I, II e VI (Plenário DECIDE por maioria absoluta, votação ostensiva), nos incisos III-V (Mesa DECLARA — ato vinculado). A banca troca frequentemente "decide" por "declara".
</div>
```

---

### FASE 7 — Revisão visual final

**Objetivo:** Abrir o `guia_ricd.html` no navegador e verificar:

1. ✅ Todas as 17 tabelas renderizam corretamente
2. ✅ Dark mode funciona para todos os novos elementos
3. ✅ Mobile (resize para 768px) mostra data-labels corretamente
4. ✅ Perguntas-âncora aparecem acima de cada tabela
5. ✅ Armadilhas CEBRASPE renderizam em grid
6. ✅ Lei Seca aparece como rodapé de cada tabela
7. ✅ Nenhum conteúdo factual foi alterado
8. ✅ O parágrafo `<p class="inc">` existente continua presente (NÃO remover)

---

## 5. INSTRUÇÕES PARA O NOVO CHAT

### Contexto a fornecer:
```
Arquivo principal: guia_ricd.html (10.000+ linhas)
Seção-alvo: "14B — Tabelas Comparativas" (linhas ~8440–8903)
CSS: linhas 13–235
Cards de referência (NÃO alterar): CARDEXEMPLO.MD e flashcard_cpi_poderes.html
Relatório de revisão (NÃO alterar): RELATORIO_REVISAO.md
```

### Regras absolutas:
1. **NÃO alterar conteúdo factual** — dados, artigos, números, texto substantivo são sagrados
2. **NÃO remover** nada existente — apenas ADICIONAR ou REFINAR
3. **Preservar `<p class="inc">`** — as notas de rodapé existentes ficam
4. **Executar fase por fase** — mostrar resultado de cada fase antes de prosseguir
5. **Ler ANTES de editar** — sempre `read_file` da seção antes de qualquer `edit`
6. **Testar dark mode** — toda classe nova precisa de variante `.dark`

### Sequência de execução:
```
FASE 0 → CSS novas classes (1 edit no <style>)
FASE 1 → data-label mobile (17 edits, 1 por tabela)
FASE 2 → tsub/tsub2 nas Tab 12-17 (6 edits)
FASE 3 → Refinamento row classes e tnum (4 edits em Tab 12, 14, 15, 17)
FASE 4 → Booleans ttag-sim/ttag-nao (1 edit em Tab 13)
FASE 5 → colspan em Tab 14, 16 (2 edits)
FASE 6A → Perguntas-âncora (17 edits, 1 por tabela)
FASE 6B → Armadilhas CEBRASPE (3-5 edits em tabelas selecionadas)
FASE 6C → Lei Seca compacta (17 edits, 1 por tabela)
FASE 6D → Alert box nuances (2-3 edits em tabelas selecionadas)
FASE 7 → Revisão visual final (browser preview)
```

**Estimativa:** ~70 edits, executáveis em 4-6 turnos de chat.
