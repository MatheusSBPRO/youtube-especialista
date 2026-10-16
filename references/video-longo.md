# Vídeo longo: o que aprendemos fazendo o primeiro

O método completo (pesquisa, pauta, título e miniatura, roteiro, edição, revisão e leitura) está em
`metodo/README.md`. Este arquivo junta as lições práticas do primeiro longo do case: um teste de
levantar do chão em 4 níveis, com 12 minutos.

## Antes de gravar

- **O título e a miniatura fecham antes do roteiro.** Se a pauta não rende um título que a pessoa
  clicaria, ela não vira vídeo. [RELATO: Paddy Galloway, Colin and Samir]
- **Um bom primeiro longo é um teste que a pessoa faz em casa, junto com o vídeo.** Ela participa,
  descobre em que nível está e comenta o resultado. O formato rende comentário, retenção e o próximo
  vídeo ("o que fazer se você ficou no nível 2").
- **O roteiro é a fala corrida completa, palavra por palavra, no teleprompter.** Lista de tópicos
  não serve: o expert lê tópico como "assunto" e não grava. O trecho técnico vai escrito de forma
  conservadora, marcado `[VALIDAR COM ESPECIALISTA]`, e o expert valida antes de gravar. O modelo
  está em `templates/roteiro-e-briefing.md`.
- **A chamada de inscrição é gravada em take separado**, em 2 versões (A e B). Assim ela entra onde
  render mais, sem regravar o resto.
- **Peça também o b-roll do dia a dia:** cenas de 5 s, sem fala, da vida real que o tema afeta.

## O que vem errado no bruto

| Armadilha | Como aparece | O que fazer |
|---|---|---|
| Câmera frontal espelha | o texto da camiseta aparece invertido | `ffmpeg -vf hflip` antes de montar |
| iPhone grava em HDR (HLG) | a cor estoura ou fica lavada no render SDR | converta para SDR (tonemap) logo na entrada |
| B-roll vertical num vídeo horizontal | barras pretas | coloque em quadro, com fundo desfocado, ou faça uma colagem lado a lado |
| Locução gravada no celular | o timbre muda em relação ao microfone de lapela | equalize, ou regrave na lapela |
| Arquivo de áudio solto na pasta | parece instrução, mas é a locução do expert | ouça e transcreva antes de decidir |
| Aluno aparece no b-roll | uso de imagem | peça a autorização por escrito antes de publicar |

## Edição

- **Monte por lista de blocos (EDL)**, um bloco por trecho do roteiro. Quando o expert pede um
  ajuste, você re-renderiza só o bloco que mudou e refaz a concatenação. Assim cada versão nova sai
  em minutos.
- **Transcreva com timestamps** (whisper local) e corte pela transcrição: onde a pessoa enrolou,
  repetiu ou errou.
- **Áudio:**
  - Mire em −14 LUFS integrado.
  - A voz passa pelo compressor **antes** de misturar a música, e depois leva um ganho linear.
  - Com o loudnorm dinâmico, ou com a música entrando antes do compressor, a pausa sem voz chegou a
    −15,5 LUFS, e o fundo "respirava".
- **Pausa de participação:** quando o vídeo pede "pause e faça o teste agora", deixe 3 a 4 s de tela
  parada com o texto. Vale a mesma coisa para os capítulos.
- **Cena com IA (quando falta take):**
  - Gere poucas, de 5 a 9 s.
  - Mostre ao expert numerada e só use a que ele aprovar.
  - Marque "conteúdo alterado ou sintético: sim" na publicação.
  - Nunca use IA no rosto do expert.
- **Versões:** v1, v2, v3… cada uma com a lista do que mudou. Guarde a anterior, porque o expert às
  vezes volta atrás.

## Pacote de publicação (vai junto com a versão final para o ok do expert)

O modelo está em `templates/pacote-publicacao.md`. Ele tem:

- o título;
- 2 miniaturas, para "Testar e comparar" no Studio;
- a descrição;
- os capítulos (começam em 0:00, no mínimo 3, cada um com pelo menos 10 s);
- o comentário fixado, com a palavra;
- o link com `utm_content=<apelido-do-video>`;
- a playlist;
- a tela final e os cards.

Depois de publicar:

- [ ] Fixe o comentário.
- [ ] Ponha o vídeo como 1º da playlist "Comece por aqui". O Studio não reordena: a ordem se muda
  pela página da playlist, no YouTube.
- [ ] Ponha o vídeo como destaque para inscritos na página inicial.
- [ ] Aponte o "vídeo relacionado" dos Shorts do mesmo tema para ele.
- [ ] Inclua o vídeo nos vídeos longos que o robô cobre (são os 6 mais recentes, automático).
- [ ] Avise o expert com o link.
