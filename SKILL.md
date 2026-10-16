---
name: youtube-especialista
description: Monta e opera o canal de YouTube de um especialista (expert de infoproduto) do zero à rotina. Cobre os Reels que já performaram virando Short (1 por dia, fila automática pelo Studio), a palavra no comentário com robô que responde, a identidade do canal (banner, foto, links com UTM, playlists, padrões de upload), o vídeo longo (título e thumb antes de gravar, roteiro em fala completa no teleprompter, edição e pacote de publicação), os Shorts na captação de lançamento e a leitura do canal. Use quando o pedido for "montar o YouTube do expert", "subir os Reels como Shorts", "robô de comentário no YouTube", "Shorts na captação", "pauta/título/thumb/roteiro de YouTube", "arrumar o canal" ou "por que o canal não cresce".
---

# YouTube do especialista

Esta skill saiu do canal de uma especialista em saúde para o público 50+. Ela tinha centenas de
Reels gravados para o Instagram e um canal parado. Os números abaixo são do Studio dela:

| Últimos 28 dias | Antes | Depois |
|---|---|---|
| Visualizações | 218 | 43,6 mil |
| Inscritos ganhos | 7 | 576 |
| Visualizações vindas do feed de Shorts | — | 82% |

- **Quando começou:** o salto veio no dia em que 9 Shorts saíram juntos. Depois, ficou 1 por dia às 19h.
- **O melhor Short:** um só trouxe 308 inscritos em 7 dias.
- **O que ainda não dá para mostrar:** venda atribuída ao YouTube. O link com UTM entrou no ar há poucos
  dias e a skill não inventa esse número.

O método do vídeo longo fica em `metodo/` (pesquisa, pauta, título e miniatura, roteiro, edição, revisão
e leitura). Cada regra traz a fonte marcada como [OFICIAL], [RELATO], [OBSERVAÇÃO] ou [HIPÓTESE]. Os
scripts que rodam no Studio ficam em `scripts/`.

---

## A ordem que deu resultado

Esta é a ordem por esforço: o que mais deu resultado com o menor trabalho vem primeiro. Não pule.

1. **Short reaproveitado de Reels que já performaram**, 1 por dia em horário fixo → `references/shorts-de-reels.md`
2. **Palavra no comentário + robô que responde** → `references/palavra-no-comentario.md`
3. **Identidade do canal.** O link do topo do canal é o único link clicável que quem vem do Short
   alcança → `references/identidade-do-canal.md`
4. **Vídeo longo.** O Short traz gente nova e o longo aquece quem chegou → `references/video-longo.md` + `metodo/`
5. **Leitura semanal** → `references/medir.md`

Para usar Shorts na captação de lançamento, leia `references/captacao-com-shorts.md` depois do passo 2.

---

## Fase 0: diagnóstico (antes de qualquer coisa)

Responda por escrito. O que faltar vira pergunta para o expert, e não suposição.

| Pergunta | Por que importa |
|---|---|
| Quem é o dono do canal, e com que conta Google você entra (dono, Administrador ou Editor no Studio)? | Os scripts entram pelo Studio com essa conta. Como Editor, não dá para mexer na identidade do canal |
| Quantos Reels existem, e quais performaram (visualizações, compartilhamentos e salvamentos no Instagram)? | A fila começa pelos que já provaram que prendem |
| Os arquivos originais estão sem a marca d'água do Instagram ou do TikTok? | Short com marca de outra plataforma tende a não ser recomendado |
| Qual é o destino: produto, captação, ou os dois? Qual é o link com UTM? | Define as palavras do robô e o 1º link do canal |
| O canal está marcado como "conteúdo para crianças"? | Se estiver, o YouTube desliga os comentários e o robô morre. Tem que ser "não" |
| Quem dá o ok do que vai a público? | Nada sai sem esse ok |
| O canal tem vídeo antigo fora de contexto (podcast velho, outro assunto)? | Não apague. Tire da página inicial e das playlists novas |

---

## Fase 1: Shorts

`references/shorts-de-reels.md`. Em resumo:

1. Separe os Reels que já performaram.
2. `montar_fila.py` gera a `fila.json` sem repetir o que já está no canal.
3. O expert aprova a fila.
4. `subir_fila.py` programa um Short por dia.
5. `conciliar.py` acerta a fila pelo que o Studio mostra.

A fila não se repõe sozinha. Marque na agenda, 5 dias antes de ela acabar, a hora de montar o lote seguinte.

## Fase 2: palavra no comentário

`references/palavra-no-comentario.md`.

- **A chamada:** todo Short termina com uma chamada única, do tipo "comenta AULA que eu te mando".
- **O robô:** `comentarios/responder.py` roda a cada 30 min e responde só o comentário curto e recente.
  Ele pula a conversa que já tem resposta.
- **O link:** link em comentário de Short não é clicável. Por isso, no Short, a resposta manda para o
  link do topo do canal. Só no vídeo longo a resposta leva o link direto.

## Fase 3: identidade do canal

`references/identidade-do-canal.md`.

- Banner, foto e descrição.
- Os links em ordem, com UTM. O 1º aparece no topo.
- Playlists, página inicial, marca d'água e padrões de upload.

Antes de trocar qualquer coisa, salve o estado atual (prints e arquivos), para poder voltar atrás.

## Fase 4: vídeo longo

Use `metodo/README.md` (as 11 etapas, com portão de aprovação antes do roteiro) e
`references/video-longo.md` (o que aprendemos gravando, editando e publicando o primeiro longo).

## Fase 5: medir

`references/medir.md`. Duas fontes:

- **`analise/coletar.mjs`:** lê a análise do Studio sem API, e o `gerar.py` monta um HTML.
- **A venda ou o lead com `utm_source=youtube`**, no checkout ou no CRM. É a única métrica de negócio.

---

## Regras inegociáveis

- **Nada vai a público sem o ok do expert:** vídeo, foto, banner, descrição ou resposta nova. Short
  sobe como privado, com data programada.
- **O Studio é a verdade, o log não.** Antes de dizer "subiu" ou "respondeu", confira no Studio.
- **Link de Short não clica.** Desde 31/08/2023, link em comentário e em descrição de Short não é
  clicável. Os links clicáveis são:
  - os links do canal (o 1º aparece no topo);
  - a descrição e os comentários de vídeo longo;
  - o "vídeo relacionado" do Short, quando aponta para um longo.

  [OFICIAL: anúncio do YouTube de agosto de 2023]
- **Use link direto com `utm_source=youtube&utm_medium=organico`.** Um encurtador que perca a UTM no
  caminho apaga a atribuição. Confira se a página repassa a UTM para o checkout ou para o formulário.
- **Não suba o mesmo vídeo duas vezes.** O `montar_fila.py` compara com o que já está no canal.
- **A automação pelo Studio não é interface oficial.** Quando o YouTube muda a tela, o seletor quebra.
  O robô então avisa e para. Não aumente os limites para acelerar: o limite existe para o canal não
  parecer spam.
- **Saúde, dinheiro e jurídico:** sem promessa de cura nem de resultado garantido, e nenhuma
  prescrição individual. Veja `metodo/README.md`, seção "Conteúdo sensível".

---

## Como acionar

```
"Faz o diagnóstico do canal do expert"                          → Fase 0
"Separa os Reels que mais performaram e monta a fila de Shorts" → Fase 1 (para na aprovação da fila)
"Liga o robô da palavra AULA"                                   → Fase 2 (config + --simular antes)
"Arruma o canal: banner, links, playlists"                      → Fase 3 (entrega o pacote, aplica depois do ok)
"Levanta 5 pautas de vídeo longo"                               → metodo/, etapas 1-4, para no portão
"Pauta aprovada, escreve o roteiro em fala completa"            → metodo/, etapa 6
"Quero usar Shorts na captação do lançamento"                   → references/captacao-com-shorts.md
"Como está o canal?" / "Por que esse vídeo não andou?"          → Fase 5
```

## Arquivos

- `references/`: shorts-de-reels · palavra-no-comentario · captacao-com-shorts · identidade-do-canal · video-longo · medir
- `metodo/`: o método do vídeo longo (README + 5 referências com fontes)
- `templates/`: análise de audiência, ficha de oportunidade, roteiro e briefing, checklist de edição, análise pós-publicação, pacote de publicação
- `scripts/`: login, fila de Shorts, robô de comentários, análise do Studio e agendamento (veja `scripts/README.md`)
