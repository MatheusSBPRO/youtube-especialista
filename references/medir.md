# Leitura do canal

## Toda semana

| Indicador | Onde | O que diz |
|---|---|---|
| Visualizações e inscritos ganhos em 28 dias, contra os 28 anteriores | Studio › Análise | se o canal está andando |
| Origem do tráfego (feed de Shorts, busca, navegação, sugeridos) | Studio › Análise › Alcance | de onde vem o público. No começo, quase tudo é feed de Shorts, e isso é normal |
| **Inscritos ganhos por vídeo** | Studio › Análise › Conteúdo | qual tema e formato trazem público. É melhor sinal do que a visualização |
| Retenção e CTR de impressão do longo | Studio › vídeo › Análise | se o título prometeu e se o vídeo cumpriu (método em `metodo/references/estrutura-e-retencao.md`) |
| Comentários com a palavra e respostas do robô | `responder.log` | interesse por tema, e se o robô está vivo |
| **Lead e venda com `utm_source=youtube`** | checkout e CRM | a única métrica de negócio. O resto é meio |

## O script

`scripts/analise/coletar.mjs` lê a análise do Studio com o login do perfil (sem API) e grava o
`dados.json`. Depois, `scripts/analise/gerar.py` monta um HTML único com:

- o crescimento;
- os inscritos;
- a origem do tráfego;
- os vídeos com mais inscritos ganhos;
- os comentários recentes.

Agende de 2 em 2 horas, ou uma vez por dia (veja `scripts/agendar/`). Se o Studio não abrir, o
script avisa e não mexe no último HTML bom.

Por que sem API: quem entra como Administrador pelo Studio não consegue a API do YouTube Analytics,
porque ela pede o login do dono. Quando quem roda é o dono, a API é o caminho mais estável.

## Como decidir com os números

As réguas abaixo são o ponto de partida. Ajuste ao canal depois de 4 semanas.

- O tema que trouxe mais inscritos em 7 dias vira o lote seguinte de Shorts e a próxima pauta de
  longo.
- Um Short com muita visualização e quase nenhum inscrito é entretenimento. Não repita o formato
  esperando inscrito.
- Um longo com CTR baixo e retenção boa tem problema de título ou miniatura, e não de conteúdo.
  Teste outra miniatura antes de mexer no vídeo.
- Um longo com CTR bom e retenção que cai no primeiro minuto não cumpriu a promessa do título na
  abertura.
- Muito comentário com a palavra e nenhum lead: o caminho até o link quebrou. Confira o 1º link do
  canal, a resposta do robô e se a UTM chega.
