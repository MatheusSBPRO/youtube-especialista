# Shorts a partir dos Reels que já performaram

## Por que começar pelo Short

O canal novo, ou parado, não tem quem assista o vídeo longo. O feed de Shorts entrega para quem
ainda não é inscrito. No case, 82% das visualizações de 28 dias vieram desse feed, e o vídeo longo
só entrou depois. [OBSERVAÇÃO: Studio do canal do case]

O expert que já tem Instagram tem o ativo pronto: Reels gravados e com número de desempenho. Não
grave nada novo para começar.

## 1. Seleção

1. Puxe os Reels dos últimos 6 a 12 meses e ordene por **compartilhamentos e salvamentos**. Use as
   visualizações para desempatar. Compartilhar e salvar dizem que o conteúdo segurou a pessoa, e
   visualização sozinha pode ser só distribuição.
2. Fora da lista:
   - Reel que depende de legenda do Instagram para fazer sentido.
   - Reel de oferta com data vencida.
   - Trend com áudio que talvez não esteja liberado no YouTube.
   - Reel com marca d'água de outra plataforma. Use o arquivo original: Short com marca do
     Instagram ou do TikTok tende a não ser recomendado. [RELATO: Creator Insider/YouTube]
3. O formato é vertical 9:16 (ou quadrado), com até 3 minutos. [OFICIAL: YouTube Help, Shorts]
4. Se o mesmo vídeo já está no canal, não entra. O `montar_fila.py` compara pelo título e pela
   duração com o que o Studio mostra.

## 2. Título e descrição

- **Título:** a frase-gancho do vídeo, como o público fala. Curto e sem clickbait que o vídeo não
  cumpre. Não precisa de `#shorts`.
- **Descrição:** 1 ou 2 linhas sobre o que o vídeo mostra, mais a chamada da palavra ("Comenta AULA
  que eu te mando o link"). **Sem URL**, porque em Short ela não clica.
- **Hashtags:** no máximo 3, do assunto.
- **Vídeo relacionado:** quando existir um vídeo longo do mesmo assunto, aponte o Short para ele (o
  campo fica nos detalhes do Short, no Studio). É o caminho clicável do Short para o longo.

## 3. Cadência

- **Comece com um lote.** No case, 9 Shorts saíram no mesmo dia, e foi o que destravou a
  distribuição. [OBSERVAÇÃO: um canal só. Trate como hipótese a testar, não como regra]
- **Depois, 1 por dia em horário fixo.** No case foi às 19h, o horário em que o público do expert
  mais aparece no Instagram. Use o horário do público do expert, não um horário genérico.
- **Programe como privado com data.** O Studio publica sozinho e nada fica público antes da hora.

## 4. A fila (scripts/shorts)

```
montar_fila.py   → lê a pasta de vídeos, tira o que já está no canal e gera a fila.json (não sobrescreve fila existente)
[o expert aprova a fila]
subir_fila.py    → sobe e programa cada item, um por dia, no horário da config. É retomável: se cair no meio, continua de onde parou
conciliar.py     → compara a fila com o Studio e acerta o estado. Rode depois de toda subida e sempre que algo parecer estranho
listar_studio.mjs → o que o Studio mostra agora (programados, públicos, rascunhos)
```

- **A fila não se repõe sozinha.** 5 dias antes do último programado, junte os Reels novos e rode o
  `montar_fila.py` com o lote seguinte.
- **Rascunho órfão:** se o computador desligar no meio de um upload, o `conciliar.py` mostra se ficou
  rascunho sem data no Studio. Programe ou apague esse rascunho antes de subir de novo.
- **Limite diário:** o YouTube limita os uploads por dia de cada canal. Se o Studio recusar, o script
  para e você continua no dia seguinte. Não insista.

## 5. O que olhar depois de 7 dias

- **O sinal é o inscrito ganho por Short, não a visualização.** Um Short com muita visualização e
  zero inscrito entretém, mas não traz público para o canal.
- O tema e o formato dos 3 Shorts que mais trouxeram inscritos viram o critério do lote seguinte e
  as primeiras pautas de vídeo longo.
- O tema que, em 5 Shorts, não trouxe inscrito sai do próximo lote. [HIPÓTESE: régua inicial, ajuste
  ao canal]
