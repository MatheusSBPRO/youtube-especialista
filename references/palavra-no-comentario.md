# Palavra no comentário e o robô que responde

## A mecânica

Todo Short termina com uma chamada só: **"Comenta AULA que eu te mando."** A palavra é curta, fácil
de escrever no celular, e cada destino tem a sua (AULA para a captação, GUIA para a isca, o nome do
produto para a venda).

O robô (`scripts/comentarios/responder.py`) roda a cada 30 minutos. Ele acha o comentário que tem a
palavra e responde com o texto da config. Na primeira rodada do case, respondeu 12 comentários que
estavam esperando.

## A limitação que muda a resposta

**Desde 31/08/2023, link em comentário e em descrição de Short não é clicável.** Fixar o comentário
não muda isso. No vídeo longo, o link na descrição e no comentário continua clicável.
[OFICIAL: anúncio do YouTube, agosto de 2023 · TechCrunch e Tubefilter, 10/08/2023]

Por isso a config tem dois textos por palavra:

| Onde | O que a resposta faz | Exemplo |
|---|---|---|
| Short (`resposta_short`) | Manda a pessoa para o **link do topo do canal**, que é clicável. Se tiver um endereço curto que dá para digitar, ele vai junto | "Te mandei! O link tá no topo do meu canal, é só tocar no meu nome 👆" |
| Vídeo longo (`resposta_longo`) | Leva o link direto, com UTM | "Aqui o link da aula: https://seusite.com/aula?utm_source=youtube&utm_medium=organico&utm_content=resposta" |

Consequência: **o 1º link do canal precisa ser o destino da palavra que está rodando.** Se a palavra
é AULA, o 1º link do canal é a página de inscrição da aula (veja `identidade-do-canal.md`).

Mesmo sem o link clicável no Short, a palavra tem valor por três motivos:

- O comentário conta como interação para o vídeo.
- A resposta tira a pessoa do feed e manda para o canal.
- O robô registra quem pediu, e isso mede o interesse por tema.

## Regras do robô (já vêm na config)

| Regra | Valor | Por quê |
|---|---|---|
| Tamanho do comentário | até 6 palavras | "AULA" e "quero a aula" são pedidos. Um parágrafo com a palavra no meio é conversa, e quem responde é o expert |
| Idade do comentário | até 21 dias | Responder pedido de 3 meses atrás com link de campanha encerrada queima |
| Por rodada | no máximo 20 | Resposta em massa num minuto parece spam para o YouTube |
| Conversa que já tem resposta | pula | Se o expert já respondeu à mão, o robô não repete |
| Variação de texto | 3 versões sorteadas | O mesmo texto 200 vezes parece robô para a pessoa e para o filtro |
| Vídeos cobertos | os Shorts recentes + os 6 vídeos longos mais novos | Comentário em vídeo velho é raro e o custo de ler é alto |
| Interruptor | arquivo `DESLIGADO` na pasta | Para tudo na hora, sem mexer no agendamento |
| Alerta | no máximo 1 a cada 6 h | Se o login cair ou a tela mudar, você sabe. Sem enxurrada |

Antes de ligar, rode `responder.py --simular`. Ele lista o que responderia e não escreve nada. Mostre
essa lista ao expert junto com os textos.

## Configurações do canal que o robô exige

- **Comentários ativados**, com "Reter comentários potencialmente inapropriados" (o nível básico).
  **Não** use "reter todos para revisão": o robô só responde comentário publicado.
- **Público do canal:** "Não, não é conteúdo para crianças". Conteúdo para crianças desliga os
  comentários.
- **A conta do robô** entra no Studio como dono ou Administrador do canal. A resposta sai com o nome
  e a foto do canal, não com os da conta pessoal. Confira isso na primeira resposta.

## O que não fazer

- Não responder com link de encurtador que perde a UTM.
- Não responder comentário negativo ou dúvida séria com o texto do robô. Isso fica para o expert, e
  a regra das 6 palavras já filtra quase tudo.
- Não usar a mesma palavra para dois destinos. Quando a campanha muda, a palavra muda.
