---
name: compilar-manual-html-comentado
description: >-
  Variante COMENTADA de compilar-manual-html: além de compilar o material-fonte
  (transcrições de aulas, apostilas, PDFs, anotações) num manual HTML
  autocontido e navegável, a IA ACRESCENTA uma camada própria de apontamentos —
  complementos, insights, dicas e sobretudo ATUALIZAÇÕES e CORREÇÕES com as
  melhores práticas atuais (datadas, com fonte), sempre em
  blocos separados do que o curso ensinou. Use SEMPRE que o usuário pedir um
  manual/apostila/guia que "complemente o material", "traga insights/dicas",
  "atualize a aula", "corrija o que foi ensinado", "aponte o que mudou / as
  melhores práticas de hoje", "comente/anote o conteúdo" ou "não só compile,
  agregue" — mesmo sem dizer HTML. Ideal quando o material pode estar datado e o
  usuário quer o curso + a visão atualizada lado a lado. Fronteira: quer
  compilação ESTRITAMENTE FIEL, sem comentário da IA → use compilar-manual-html;
  quer ESCOLHER recortes/filtros → use compilar-manual-html-com-filtros. NÃO use
  para resumo curto no chat, .docx formal ou peça jurídica.
---

# Compilar manual HTML — comentado (com apontamentos da IA)

Mesma entrega da skill base `compilar-manual-html` — **um `.html` autocontido, denso, navegável, com prompts copiáveis** — com **uma diferença central**: além de compilar fielmente, você **acrescenta uma camada de apontamentos da IA**. O manual passa a ter **duas vozes lado a lado**:

- **Camada-fonte** — o que o curso/material ensinou, fiel (regra de fidelidade da base).
- **Camada-IA** — o que **você** acrescenta: complementos que preenchem lacunas, insights, dicas, e principalmente **atualizações** (o que mudou desde a aula) e **correções** (o que a aula ensinou de forma imprecisa ou datada), trazendo as **melhores práticas atuais**.

> Por que isso importa: material de curso envelhece — ferramentas somem, preços mudam, uma técnica vira antipadrão. O aluno quer o que foi ensinado **e** a leitura atualizada, sem confundir uma coisa com a outra. O valor da variante está em **agregar sem adulterar**: a fonte permanece intacta; a IA comenta ao lado, sempre identificada.

O **motor de montagem** (extração → arquitetura → HTML do template → índices → validação) é o mesmo da base. O que muda e o que você precisa dominar está aqui. Os blocos visuais estão em `references/componentes.md` (com o componente **Apontamento da IA** já pronto). O esqueleto com CSS/JS está em `assets/template.html` (já traz o CSS violeta da camada-IA). **Não reescreva CSS/JS.**

---

## As duas camadas (leia isto antes de tudo)

Todo o resto da skill serve a esta distinção. Grave-a:

| | Camada-fonte | Camada-IA (apontamentos) |
|---|---|---|
| **O que é** | O que o curso ensinou | O que a IA acrescenta |
| **Cor** | Paleta normal do tema | **Violeta** (exclusiva) |
| **Regra** | Fidelidade: não invente, não "melhore" | Acréscimo honesto, atribuído e (p/ atualização/correção) **verificado** |
| **Componente** | callouts, prompts, pipelines, cards, tabelas | `.ianote` (4 subtipos) |
| **Índice** | Sumário temático, Sumário de prompts | **Índice de apontamentos** |

**A regra de ouro:** o leitor deve saber, em qualquer ponto, se está lendo o curso ou a IA. Onde há violeta, é a IA falando. Você **nunca** reescreve a fala do curso por dentro para embutir sua opinião — a fonte fica fiel, e o apontamento vem num bloco à parte, ao lado.

### Os quatro subtipos de apontamento

- **Complemento** — preenche uma lacuna: um pressuposto que a aula pulou, um passo omitido, um "como" que ficou implícito. Abra sinalizando: *"A aula não detalha isto, mas…"*.
- **Insight** — conexão / porquê: amarra dois tópicos, explica a intuição por trás, dá a leitura de quem já domina o assunto.
- **Atualização** — algo **mudou desde a aula**: a ferramenta foi descontinuada, o preço/limite mudou, surgiu uma opção melhor, a recomendação da comunidade virou. Formato "Na aula X → Hoje Y". **Exige data e, quando possível, fonte.**
- **Correção** — a aula ensinou algo **impreciso ou errado**. Formato "A aula afirma X → Correto: Y". **Exige data e fonte.** Use com parcimônia e só com confiança real (veja o aterramento abaixo).

---

## Aterramento: como não alucinar "as melhores práticas atuais"

Este é o risco número um da variante. "Atualize a aula com as melhores práticas de hoje" convida o modelo a inventar fatos e a apresentar como "atual" algo que já é a memória datada do próprio modelo. Discipline-se:

1. **Verifique antes de atualizar/corrigir.** Não afirme "hoje recomenda-se X", "a ferramenta mudou", "o preço agora é Y" a partir da memória. Confirme em fonte externa — use as ferramentas disponíveis: busca web / Perplexity para preços, versões, descontinuações; `context7` para docs de bibliotecas/frameworks/SDKs; a doc oficial do produto. Só então escreva o apontamento.
2. **Date sempre.** Toda atualização/correção leva "Verificado em [mês/ano]" — porque a prática volta a mudar. A data protege o leitor e você.
3. **Cite fonte real, nunca fabricada.** Se confirmou, linke a fonte. Se **não** conseguiu confirmar, **não invente link** e **não afirme correção**: rebaixe para um **Complemento** em tom de "vale verificar — indício de que isto pode ter mudado", que é honesto.
4. **Seja conservador na correção.** Corrigir o instrutor é forte. Só faça quando tiver confiança + fonte. Divergência de opinião não é "correção" — é, no máximo, um Insight que apresenta a visão alternativa. Erro factual verificável é correção.
5. **Preserve a fonte mesmo ao corrigir.** Registre o que a aula disse (para o aluno reconhecer) e ao lado o certo. Nunca apague/reescreva a fala original para "consertá-la" silenciosamente.
6. **Curadoria humana em áreas sensíveis.** Jurídico, saúde, finanças, tributário: reforce em `callout warn` que atualização/correção da IA é ponto de partida a validar com profissional/fonte primária — não conselho definitivo.

Se as ferramentas de verificação não estiverem disponíveis, diga-o ao usuário e ofereça duas saídas: (a) gerar o manual com apontamentos **conservadores** (só complementos/insights que não dependem de fato datado, e atualizações marcadas como "a confirmar"), ou (b) aguardar para verificar. Não force correções não verificadas.

---

## Método (siga na ordem)

O esqueleto é o da base; os passos marcados **[IA]** são o que esta variante acrescenta.

### Passo 1 — Leia TUDO, por inteiro
Leia cada arquivo-fonte completo (use a skill de leitura por tipo). Sem o todo, você não sabe o que a aula pressupõe, onde deixa lacunas e o que envelheceu. Entrada típica: arquivos em `/mnt/user-data/uploads/` ou o caminho que o usuário indicar.

### Passo 2 — Trave o recorte (o filtro)
Confirme em uma frase o critério que decide o que entra (ex.: "só o que ensina uso de IA"). O recorte é a lei do manual: fora dele, descarte; dentro, seja exaustivo. Se não estiver claro, faça **uma** pergunta.

### Passo 2-IA — Combine a intensidade dos apontamentos
Pergunte (uma `AskUserQuestion`, ou assuma o padrão e diga que assumiu) **quanto** a IA deve acrescentar. Isto calibra a densidade da camada violeta:

- **Enxuto** — só o essencial: correções e atualizações que realmente importam. Poucos complementos.
- **Equilibrado (padrão recomendado)** — atualizações + correções + complementos que destravam a prática + insights pontuais. É o ponto doce para a maioria.
- **Companheiro de estudo** — camada rica: complementa, conecta, aprofunda e atualiza generosamente, como um tutor anotando a apostila.

Em qualquer nível, atualização e correção **sempre** seguem a regra de aterramento. A intensidade regula volume, não rigor.

### Passo 3 — Extraia para um inventário estruturado (camada-fonte)
Varra o material e capture só o que cai no recorte: **tópico**, **ferramentas/apps**, **prompts exatos** (verbatim na substância; limpe só ruído de fala; guarde variações), **passo a passo** de cada workflow, **fatos/números/definições** para o glossário. Este inventário é a camada-fonte, fiel.

### Passo 3-IA — Levante os "candidatos a apontamento"
Numa **segunda passada**, agora com olhar crítico e atual, marque no inventário onde a IA agrega valor:
- **Lacunas** → candidatos a *Complemento* (a aula assume um passo/conceito sem explicar).
- **Conexões/porquês** → candidatos a *Insight*.
- **Cheiro de datado** → candidatos a *Atualização*: menção a versões, preços, planos, "recentemente", nomes de ferramentas, limites, "a novidade é". Marque para **verificar** no Passo seguinte.
- **Afirmação que soa imprecisa/errada** → candidato a *Correção*: marque para **verificar**.

Você terá uma lista de candidatos. Ainda não escreva os apontamentos — falta verificar.

### Passo 3-V — Verifique os candidatos datados/duvidosos
Para cada candidato a **atualização** ou **correção**, confirme em fonte externa (ver "Aterramento"). Resultado de cada um:
- Confirmado → vira apontamento com data + link.
- Não confirmado, mas com indício → vira Complemento "vale verificar", sem afirmar.
- Refutado (a aula estava certa) → descarte o candidato; não crie apontamento.

Faça as verificações em paralelo quando possível para não travar. Complementos/insights que não dependem de fato datado não precisam desta etapa.

### Passo 4 — Desenhe a arquitetura de tópicos
Agrupe o inventário em poucos tópicos grandes (A, B, C…), cada um com subseções numeradas e workflows como pipelines. Defina os `id`s agora. Os apontamentos moram **dentro** da subseção a que se referem (ao lado do trecho comentado), e os importantes ganham `id="ap-..."` para o Índice de apontamentos. Ordem típica: Abertura → Como usar (com a legenda, incluindo o item **◆ IA**) → Mapa de ferramentas → tópicos → Referência (Glossário, Sumário temático, Sumário de prompts, **Índice de apontamentos**).

### Passo 5 — Monte o HTML a partir do template
1. Copie `assets/template.html` para o diretório de trabalho.
2. Re-tematize `:root` por assunto (mantendo a família **violeta** da camada-IA — ela é a assinatura da variante; não a troque pela cor de acento do tema, senão a distinção some).
3. Preencha o `<nav>` (um `.navgroup` por tópico; inclua o link **Índice de apontamentos da IA**, já presente no template).
4. Construa as seções com os componentes de `references/componentes.md`. Em arquivos grandes, **anexe seção por seção** (`cat >> arquivo << 'HTMLEOF' … HTMLEOF`).
5. Intercale os `.ianote` ao lado dos trechos que comentam. Dê `id` = `data-copy` a cada bloco de prompt; dê `id="ap-..."` a cada apontamento indexável.

### Passo 5-IA — Prompts: original fiel + versão da IA (quando couber)
O prompt do material entra **verbatim** (camada-fonte). Se você tem uma versão melhor (mais robusta, com placeholders melhores, adaptada a uma ferramenta atual), acrescente-a como **um segundo bloco de prompt**, precedido de um `.ianote` curto ("Versão da IA: por que muda"). Mantenha os dois — o aluno compara. Nunca substitua o original silenciosamente.

### Passo 6 — Os índices + glossário
- **Glossário** (`#glossario`), **Sumário temático** (`#sumario-tematico`), **Sumário de prompts** (`#sumario-prompts`): como na base.
- **Índice de apontamentos** (`#apontamentos`) **[IA]**: liste **todas** as atualizações e correções (o valor central), depois complementos/insights indexados. Componente na seção 12 de `componentes.md`.

### Passo 7 — JS já vem pronto
Botão copiar, scrollspy e menu mobile já estão no template. Só garanta que cada `.prompt` tem `.copybtn` e `data-copy`. Os `.ianote` não precisam de JS.

### Passo 8 — Valide antes de entregar
Rode as checagens (Python/bash) e corrija:
- Balanceamento de tags; todo `href="#x"` tem `id="x"`; ids do menu batem com as seções; nenhum heredoc vazado.
- Cada bloco de prompt tem `id` = `data-copy`.
- **[IA]** Toda `.ianote.atualizacao` e `.ianote.correcao` tem `.isrc` com **data** (e link quando houver); nenhuma afirma correção sem verificação.
- **[IA]** Nenhum trecho da camada-fonte usa a cor/família violeta; nenhum apontamento está embutido na fala do curso.
- **[IA]** Todo apontamento com `id="ap-..."` aparece no Índice de apontamentos, e vice-versa.

```python
import re
h = open('Manual comentado - xxx.html', encoding='utf-8').read()
ids   = set(re.findall(r'id="([^"]+)"', h))
hrefs = {x for x in re.findall(r'href="#([^"]+)"', h) if x}
print('links quebrados:', sorted(hrefs - ids) or 'nenhum')
for t in ['div','section','main','script']:
    o=len(re.findall(rf'<{t}(?:\s|>)',h)); c=len(re.findall(rf'</{t}>',h))
    print(t, o, c, 'OK' if o==c else 'MISMATCH')
# apontamentos de atualização/correção sem linha de fonte/data:
notes = re.findall(r'<div class="ianote (atualizacao|correcao)".*?</div>\s*</div>', h, re.S)
print('atualizacao/correcao sem .isrc:', sum(1 for n in notes if 'isrc' not in n))
```

### Passo 9 — Salve e apresente
Convenção de nome: `Manual comentado - [assunto].html` (higienize `: \ / ? * < > |`, que quebram nome no Windows). Salve junto ao material-fonte ou onde o usuário indicar. Em ambiente local (CLI), apresente com `SendUserFile`; em sandbox (`/mnt/user-data/outputs/`), com `present_files`. Feche curto e ofereça ajustes (ex.: aumentar/reduzir a intensidade dos apontamentos).

---

## Identidade visual

Fuja do "cara de IA genérico". Dê identidade ligada ao assunto, alto contraste, uma cor de acento — re-tematizando só o `:root`. **Exceção inviolável:** a família **violeta** (`--ia*`) é reservada à camada de apontamentos e não deve colidir com a cor de acento do tema. Se o assunto pedir violeta como acento, desloque a camada-IA para outro tom frio distinto (ex.: índigo/ardósia) — o que não pode é fonte e IA parecerem a mesma coisa.

---

## Princípios de conteúdo

- **Fidelidade na camada-fonte.** Não invente prompts, ferramentas, números ou passos do curso. Limpe ruído, não crie substância.
- **Honestidade na camada-IA.** Acréscimo é bem-vindo; invenção não. Atualização/correção verificada e datada; do contrário, não afirme.
- **Sempre atribuível.** A cada linha, o leitor sabe se é curso ou IA. Essa é a promessa da variante.
- **Recorte acima de tudo.** Fora do recorte, corte (registre em uma linha se for vizinho importante).
- **Exaustivo dentro do recorte** — inclusive nos apontamentos que o recorte justifica.
- **Intensidade calibra volume, não rigor.** Mesmo no "enxuto", a verificação de atualização/correção é obrigatória.

---

## Anti-exemplos (quando NÃO usar esta variante)

- Usuário quer **compilação estritamente fiel, sem comentário da IA** → use a base `compilar-manual-html`.
- Usuário quer **escolher recortes/filtros** antes de montar → use `compilar-manual-html-com-filtros`.
- Pedido de **resumo curto** para o chat → prosa, sem arquivo.
- **.docx formal** → skill `docx`. **Peça jurídica** → skills de petição.
- Material que cabe em poucos parágrafos → manual navegável é exagero.
