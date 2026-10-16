# youtube-especialista

Skill do [Claude Code](https://claude.com/claude-code) para montar e operar o canal de YouTube de um
especialista (expert de infoproduto): Shorts a partir dos Reels que já performaram, palavra no
comentário com robô que responde, identidade do canal, vídeo longo e leitura.

Saiu de um canal real, o de uma especialista em saúde 50+:

- **Visualizações:** de 218 para 43,6 mil em 28 dias.
- **Inscritos ganhos:** de 7 para 576, no mesmo período.
- **Origem:** 82% das visualizações vieram do feed de Shorts.

O vídeo longo entrou depois, para aquecer quem chegou.

## A ordem

1. **Reels que já performaram viram Short**, 1 por dia em horário fixo.
2. **Palavra no comentário** ("comenta AULA"), com um robô que responde a cada 30 min.
3. **Canal arrumado.** O 1º link do canal é o destino da palavra, e é o único link clicável que
   quem vem do Short alcança.
4. **Vídeo longo:** título e thumb antes de gravar, roteiro em fala completa no teleprompter.
5. **Leitura semanal:** inscrito ganho por vídeo e lead com `utm_source=youtube`.

## Instalação

Requisitos: Claude Code, Node 18+, Python 3.10+, `ffmpeg` e `yt-dlp`. Você também precisa de uma conta
Google com acesso ao canal pelo Studio, como dono ou Administrador.

```bash
git clone https://github.com/MatheusSBPRO/youtube-especialista ~/.claude/skills/youtube-especialista
cd ~/.claude/skills/youtube-especialista/scripts
npm install && npx playwright install chromium
cp config.example.json config.json   # preencha canal, palavras, links e horário
node entrar.mjs                      # abre o navegador: faça login 1 vez na conta que gerencia o canal
```

Depois, no Claude Code:

```
Usa a skill youtube-especialista e faz o diagnóstico do canal do meu expert
```

A partir daí ele segue as fases do `SKILL.md`. Os comandos de cada script estão em
`scripts/README.md`.

## O que tem aqui

| Pasta | O quê |
|---|---|
| `SKILL.md` | o fluxo, as fases e as regras |
| `references/` | Shorts de Reels, palavra no comentário, Shorts na captação, identidade do canal, vídeo longo, leitura |
| `metodo/` | o método do vídeo longo, com as fontes (doc oficial do YouTube, Paddy Galloway, Colin and Samir, Film Booth e outros) |
| `templates/` | ficha de oportunidade, roteiro, checklist de edição, pacote de publicação, análise pós-publicação |
| `scripts/` | login, fila de Shorts, robô de comentários, análise do Studio e agendamento |

## Avisos

- **Link em comentário e em descrição de Short não é clicável** desde agosto de 2023. Por isso, no
  Short, o robô manda a pessoa para o link do topo do canal.
- **Os scripts usam o YouTube Studio pelo navegador (Playwright), e não uma API oficial.** Quando o
  YouTube muda a tela, um seletor quebra. O script então avisa e para, e o conserto fica em
  `scripts/comum/seletores`. O uso é por sua conta.
- **Nada vai a público sem o ok do expert.** Os Shorts sobem privados, com data programada.
- **O `config.json` e a pasta do perfil do navegador** ficam fora do git, porque guardam o login. Não
  suba esses arquivos.

---

Montado pela [Blessy Mídias](https://blessymidias.com.br).
