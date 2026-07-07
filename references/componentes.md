# Catálogo de componentes

Todos os blocos visuais do manual, prontos para copiar e colar dentro de `<section class="block" id="...">`. As classes já existem no CSS de `assets/template.html` — **não reescreva CSS**, só use estas classes. Campos a personalizar vêm entre `[colchetes]`.

Índice:
1. Cabeçalhos de seção e tópico
2. Frase-síntese (keyidea)
3. Callouts (skill / app / tip / warn) e tags inline
3-IA. **Apontamento da IA** (complemento / insight / atualização / correção) — exclusivo desta variante
4. Bloco de prompt (com botão copiar)
5. Pipeline (passo a passo numerado)
6. Cards de ferramentas
7. Tabela
8. Legenda de cores
9. Índices (sumário temático e de prompts)
10. Glossário
11. Miudezas (listas, links inline, lead-in, divisória)
12. **Índice de apontamentos da IA** — exclusivo desta variante

---

## 1. Cabeçalhos de seção e tópico

Abertura de cada `<section>` (o número/rótulo fica em mono, pequeno, acima do título):

```html
<div class="sechead">
  <span class="secnum">A — TÓPICO</span>
  <h2 class="sec">[Título do tópico]</h2>
  <p class="sub">[Subtítulo de 1–2 linhas explicando o tópico.]</p>
</div>
```

Para os blocos de referência use rótulos como `R1 — GLOSSÁRIO`. Para fundamentos, numeração `00 —`, `01 —`, `02 —`.

Subtópico dentro da seção (A.1, A.2...):

```html
<h3 class="topic" id="a1-xxx"><span class="tnum">A.1</span>[Título do subtópico]</h3>
```

Subdivisão menor (sem numeração) e agrupador de itens em índices:

```html
<h4 class="mini">[Rótulo curto]</h4>
```

---

## 2. Frase-síntese (keyidea)

Citação/ideia âncora destacada. Uma por seção, no máximo.

```html
<div class="keyidea"><p>“[Frase de efeito que resume a tese da seção.]”</p><div class="src">[atribuição/contexto]</div></div>
```

---

## 3. Callouts e tags inline

Caixa colorida por tipo. Quatro variantes — escolha pela natureza do conteúdo:

```html
<!-- skill (verde) — quando o ponto é uma habilidade/skill da IA -->
<div class="callout skill"><div class="clab">Skill</div><p>[O que a skill faz.]</p></div>

<!-- app (azul) — quando indica qual ferramenta/app usar -->
<div class="callout app"><div class="clab">Ferramenta</div><p>Use o <span class="apptag">Nome do App</span> para [...].</p></div>

<!-- tip (âmbar) — dica prática, atalho, observação de custo -->
<div class="callout tip"><div class="clab">Dica</div><p>[Texto da dica.]</p></div>

<!-- warn (vermelho) — atenção, risco, limite, curadoria humana -->
<div class="callout warn"><div class="clab">Atenção</div><p>[Alerta importante.]</p></div>
```

Tags inline (use no meio do texto para marcar app ou skill):

```html
<span class="apptag">ChatGPT</span>
<span class="skilltag">nome-da-skill</span>
```

---

## 3-IA. Apontamento da IA (camada de comentário) — componente-chave desta variante

O bloco que **separa o que o curso ensinou do que a IA acrescenta**. Cor **violeta** exclusiva: onde há violeta, é acréscimo da IA, não fala da fonte. Quatro subtipos — escolha pela natureza do acréscimo:

- **Complemento** (sem modificador) — preenche uma lacuna, explica um pressuposto que a aula pulou.
- **Insight** (sem modificador, rótulo `Insight`) — conexão, porquê, leitura mais profunda que amarra pontos.
- **Atualização** (`.atualizacao`, teal) — a aula ficou datada; registra a prática atual. **Exige** linha `.isrc` com **data** e, quando houver, **fonte**.
- **Correção** (`.correcao`, tijolo) — a aula ensinou algo impreciso/errado; registra o certo. **Exige** `.isrc` com data e fonte. Use com parcimônia e só com confiança.

```html
<!-- COMPLEMENTO — acréscimo explicativo -->
<div class="ianote">
  <div class="ihead"><span class="ibadge">◆ IA</span><span class="ilab">Complemento</span></div>
  <p>[Explicação que a IA acrescenta. Deixe explícito que é acréscimo — ex.: "A aula não detalha isto, mas..."]</p>
</div>

<!-- INSIGHT — conexão / porquê -->
<div class="ianote">
  <div class="ihead"><span class="ibadge">◆ IA</span><span class="ilab">Insight</span></div>
  <p>[Leitura mais profunda: por que isso importa, como se conecta a outro tópico.]</p>
</div>

<!-- ATUALIZAÇÃO — algo mudou desde a aula. id para o Índice de apontamentos. -->
<div class="ianote atualizacao" id="ap-xxx">
  <div class="ihead"><span class="ibadge">◆ IA</span><span class="ilab">Atualização</span></div>
  <p><span class="was">Na aula:</span> [o que era ensinado]. <span class="now">Hoje:</span> [a prática atual e por quê].</p>
  <div class="isrc">Verificado em [mês/ano] · Fonte: <a href="[url]">[fonte]</a></div>
</div>

<!-- CORREÇÃO — a aula errou/imprecisou. id para o Índice de apontamentos. -->
<div class="ianote correcao" id="ap-yyy">
  <div class="ihead"><span class="ibadge">◆ IA</span><span class="ilab">Correção</span></div>
  <p><span class="was">A aula afirma:</span> [afirmação imprecisa]. <span class="now">Correto:</span> [correção]. [por quê, em 1 frase]</p>
  <div class="isrc">Verificado em [mês/ano] · Fonte: <a href="[url]">[fonte]</a></div>
</div>
```

Regras de uso (o coração da variante — leia junto ao SKILL.md):
- **Nunca misture camadas.** O apontamento é um bloco à parte; jamais reescreva a fala do curso "por dentro" para embutir sua opinião. A fonte permanece fiel; a IA comenta ao lado.
- **Atribua sempre.** O leitor deve saber, a cada linha, se aquilo é do curso ou da IA. Os rótulos `Na aula:` / `Hoje:` / `Correto:` (classes `.was`/`.now`) tornam isso explícito.
- **Ancore atualização e correção.** Toda `.atualizacao` e `.correcao` carrega `.isrc` com **data** e, sempre que possível, **link de fonte verificada** — a memória do modelo tem corte temporal e "hoje" pode estar velho. Sem verificação, rebaixe para um Complemento em tom de "vale checar", não afirme correção.
- **Dê `id="ap-..."`** a toda atualização/correção (e a complementos/insights que valham indexar) para o **Índice de apontamentos** (seção 12) linkar.
- **Não invente fonte.** Se não confirmou, não cite. Um apontamento honesto sem link vale mais que um link fabricado.

---

## 4. Bloco de prompt (com botão copiar)

O componente mais importante. **Todo prompt precisa de `id` E `data-copy` idênticos** — o `id` é o destino do "Sumário de prompts"; o `data-copy` é lido pelo JS do botão copiar. Use ids descritivos e únicos: `prompt-minibio`, `prompt-triagem`, etc.

Os trechos que o usuário deve substituir vão em `<span class="ph">[ASSIM]</span>`.

```html
<div class="prompt" id="prompt-xxx" data-copy="prompt-xxx">
  <div class="pbar"><span class="ptag"><span class="dot"></span>Prompt</span><span class="plabel"> [rótulo curto · qual app/skill · o que anexar]</span><button class="copybtn">copiar</button></div>
  <pre>[Texto integral do prompt. Preserve o conteúdo; limpe só ruído de transcrição.
Use <span class="ph">[PLACEHOLDER]</span> nos campos a personalizar.]</pre>
</div>
```

Regras de extração de prompts:
- **Verbatim na substância.** Não invente nem "melhore" o prompt do material. Corrija só pontuação/ruído de fala (ditado).
- Um bloco por prompt. Se o material ensina um prompt-base e depois um "prompt de uso/ajuste", crie dois blocos.
- O `<pre>` preserva quebras de linha — escreva o prompt já formatado como deve ser colado.

---

## 5. Pipeline (passo a passo numerado)

Para todo workflow "faça X, depois Y". Cada passo é um cartão numerado; `.meta` (opcional) é um rótulo pequeno no rodapé do passo.

```html
<div class="pipe">
  <div class="step"><div class="snum">1</div><h5>[Título do passo]</h5><p>[O que fazer.]</p><div class="meta">[rótulo opcional]</div></div>
  <div class="step"><div class="snum">2</div><h5>[Título do passo]</h5><p>[O que fazer.]</p></div>
  <div class="step"><div class="snum">3</div><h5>[Título do passo]</h5><p>[O que fazer.]</p></div>
</div>
```

---

## 6. Cards de ferramentas

Grade de cartões para o "Mapa de ferramentas". `.tname` = nome, `.trole` = função curta, depois um `<p>` de descrição.

```html
<div class="tools">
  <div class="tool"><div class="tname">[Nome]</div><div class="trole">[Função curta]</div><p>[O que é e quando usar.]</p></div>
  <div class="tool"><div class="tname">[Nome]</div><div class="trole">[Função curta]</div><p>[O que é e quando usar.]</p></div>
  <!-- ...quantos cartões precisar... -->
</div>
```

---

## 7. Tabela

Para comparações (ex.: "modo × o que faz × quando usar").

```html
<table class="tbl">
  <thead><tr><th>[Col 1]</th><th>[Col 2]</th><th>[Col 3]</th></tr></thead>
  <tbody>
    <tr><td><b>[item]</b></td><td>[...]</td><td>[...]</td></tr>
    <tr><td><b>[item]</b></td><td>[...]</td><td>[...]</td></tr>
  </tbody>
</table>
```

---

## 8. Legenda de cores

Use uma vez, na seção "Como usar", para explicar o código de cores. Os `.chip` reaproveitam as cores dos callouts/prompt.

```html
<div class="legend">
  <h4>Legenda dos blocos</h4>
  <div class="legrid">
    <div class="legitem"><span class="chip prompt">Prompt</span><span>Texto pronto para copiar, com botão <b>copiar</b>. Trechos em <b style="color:var(--brass)">destaque</b> são para substituir.</span></div>
    <div class="legitem"><span class="chip skill">Skill</span><span>Uma habilidade/automação da IA.</span></div>
    <div class="legitem"><span class="chip app">Ferramenta</span><span>Qual app usar.</span></div>
    <div class="legitem"><span class="chip tip">Dica</span><span>Atalho ou observação prática.</span></div>
    <div class="legitem"><span class="chip warn">Atenção</span><span>Risco, limite ou ponto de curadoria humana.</span></div>
    <div class="legitem"><span class="chip ia">◆ IA</span><span>Acréscimo da IA (violeta): complemento, insight, <b>atualização</b> ou <b>correção</b> — <b>não</b> é fala do curso. Atualizações e correções trazem data e fonte.</span></div>
  </div>
</div>
```

O item **◆ IA** na legenda é obrigatório nesta variante: é ele que ensina o leitor a distinguir a camada-fonte da camada-IA logo na abertura.

---

## 9. Índices (sumário temático e de prompts)

Mesma estrutura para os dois. Cada linha: link (negrito) + descrição + localização (mono, à direita). Agrupe com `<h4 class="mini">`.

```html
<h4 class="mini">[Grupo]</h4>
<div class="idx">
  <div class="idxrow"><a href="#destino">[Ação / nome]</a><span class="idxdesc">[1 linha de contexto.]</span><span class="idxloc">[A.1]</span></div>
  <div class="idxrow"><a href="#destino">[Ação / nome]</a><span class="idxdesc">[1 linha de contexto.]</span><span class="idxloc">[A.2]</span></div>
</div>
```

- **Sumário temático** (`id="sumario-tematico"`): linhas no formato "quero fazer X" → link para a seção. Pense nas intenções práticas do leitor.
- **Sumário de prompts** (`id="sumario-prompts"`): uma linha por prompt, `href` apontando para o **id do bloco de prompt** (ex.: `#prompt-minibio`). Liste TODOS os prompts.

---

## 10. Glossário

Lista de definição. Ordene alfabeticamente. `id="glossario"`.

```html
<dl class="gloss">
  <dt>[Termo]</dt>
  <dd>[Definição curta e clara, com remissão à seção quando útil — ex.: Ver A.3.]</dd>

  <dt>[Termo]</dt>
  <dd>[Definição.]</dd>
</dl>
```

---

## 11. Miudezas

```html
<!-- parágrafo de entrada de seção, maior -->
<p class="lead-in">[Frase de abertura do tópico.]</p>

<!-- link interno no meio do texto -->
veja em <a class="inl" href="#b4-xxx">B.4 — [nome]</a>

<!-- listas sem bullet pesado -->
<ol class="clean"><li>[...]</li><li>[...]</li></ol>
<ul class="clean"><li>[...]</li><li>[...]</li></ul>

<!-- divisória discreta entre grandes partes -->
<div class="divider-note">[texto curto em maiúsculas]</div>
```

---

## 12. Índice de apontamentos da IA

Mesma mecânica dos outros índices (seção 9), numa seção própria `id="apontamentos"`. Reúne **tudo que a IA acrescentou** — com destaque para **atualizações** e **correções** —, para o leitor que fez o curso saber num relance o que mudou/foi corrigido. Cada linha aponta para o `id="ap-..."` do apontamento.

```html
<section class="block" id="apontamentos">
  <div class="sechead">
    <span class="secnum">R4 — APONTAMENTOS DA IA</span>
    <h2 class="sec">Índice de apontamentos da IA</h2>
    <p class="sub">O que a IA acrescentou, atualizou ou corrigiu em relação ao material original. Violeta = acréscimo da IA.</p>
  </div>

  <h4 class="mini">Atualizações &amp; correções (prioritário)</h4>
  <div class="idx">
    <div class="idxrow"><a href="#ap-xxx">Atualização · [assunto]</a><span class="idxdesc">[o que mudou desde a aula].</span><span class="idxloc">[A.2]</span></div>
    <div class="idxrow"><a href="#ap-yyy">Correção · [assunto]</a><span class="idxdesc">[o que foi corrigido].</span><span class="idxloc">[B.1]</span></div>
  </div>

  <h4 class="mini">Complementos &amp; insights</h4>
  <div class="idx">
    <div class="idxrow"><a href="#ap-zzz">Insight · [assunto]</a><span class="idxdesc">[a conexão acrescentada].</span><span class="idxloc">[C.3]</span></div>
  </div>
</section>
```

Liste **todas** as atualizações e correções (são o valor central da variante). Complementos/insights, liste os que ganharam `id`.

---

## Lembrete de consistência

- Todo `href="#x"` precisa ter uma `id="x"` correspondente. Verifique ao final.
- Os ids do menu lateral devem bater exatamente com os ids das seções.
- Cada bloco de prompt: `id` = `data-copy`, ambos únicos e descritivos.
- Toda `.ianote.atualizacao` e `.ianote.correcao` tem `.isrc` (data + fonte quando houver) e, se indexada, `id="ap-..."`.
- A camada-fonte nunca usa a cor violeta; a camada-IA nunca é embutida na fala do curso.
- Não invente CSS novo; combine as classes acima.
