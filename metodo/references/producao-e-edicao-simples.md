# Produção e edição simples — 1 vídeo por semana, 1 câmera

Operação mínima viável: uma pessoa, uma câmera, um vídeo por semana. Tudo aqui parte disso.

## 1. O que a produção precisa resolver (e só isso)

| Item | Mínimo aceitável | Não vale a pena perseguir |
|---|---|---|
| Áudio | Inteligível, sem eco forte, nível constante | Estúdio tratado |
| Imagem | Rosto iluminado, foco correto, fundo que não distrai | Segunda câmera, gimbal |
| Enquadramento | Um plano fixo bem escolhido | Troca de ângulo a cada frase |
| Apoio visual | Só onde a palavra não dá conta | Motion graphics em tudo |

Produção "bonita" vem depois da decisão do que vai ser dito. O tempo de planejamento é que carrega
o resultado em canal pequeno. [RELATO — Ed Lawrence, via Starter Story]

## 2. Gravação semanal x gravação em lote

| | Semanal (1 por vez) | Lote (3-4 de uma vez) |
|---|---|---|
| A favor | Pauta reage ao que aconteceu na semana; aprende rápido entre vídeos | Um setup só; menos troca de contexto; cobre imprevisto e férias |
| Contra | Setup toda semana; um imprevisto derruba a publicação | Pauta envelhece na gaveta; erro de método se repete nos 4 antes de descobrir |
| Quando usar | Canal começando, ainda calibrando formato e packaging | Formato já estabilizado, pauta evergreen |

Recomendação prática: **semanal nos primeiros vídeos, lote depois que o formato estabilizou** — e
mesmo em lote, nunca gravar em lote pauta sensível ao tempo. O relato de Paddy Galloway de
"estabelecer o canal" em algumas dezenas de vídeos antes de otimizar pesado vale aqui: no começo o
ganho vem de aprender a produzir. [RELATO — Paddy Galloway]

Em lote, varie roupa/enquadramento entre vídeos e refaça a abertura de cada um do zero — abertura
copiada em série fica igual e o espectador percebe.

## 3. Edição assistida — o que a máquina realmente faz

Ferramentas (todas gratuitas e locais):

| Ferramenta | Para quê | Como instalar |
|---|---|---|
| `ffmpeg`, `ffprobe` | Corte, concatenação, reenquadre, normalização de áudio, render | `brew install ffmpeg` (macOS) · `apt install ffmpeg` (Linux) |
| `yt-dlp` | Baixar vídeo e comentário público do próprio canal para análise | `brew install yt-dlp` · `pipx install yt-dlp` |
| `mlx-whisper` (Mac Apple Silicon) ou `faster-whisper` | Transcrição local com timestamps | `pip install mlx-whisper` · `pip install faster-whisper` |
| YouTube Studio › Análise | Retenção, CTR de impressão, origem do tráfego | Já vem no canal |

Se alguma dessas situações mudar, atualizar esta tabela antes de prometer o nível correspondente.

### Os 4 níveis

| Nível | O que é | Possível aqui? | Depende de |
|---|---|---|---|
| 1 | **Analisar transcrição** — transcrever e ler o que foi dito, com timestamps | Sim, local, custo zero (`mlx-whisper` / `faster-whisper`) | Receber o arquivo de áudio/vídeo |
| 2 | **Propor lista de cortes com timecode** — onde enrolou, repetiu, errou | Sim, a partir da transcrição com timestamps | Nível 1 concluído |
| 3 | **Executar os cortes** — gerar o arquivo cortado | Sim, `ffmpeg` | Arquivo em disco **e autorização explícita** |
| 4 | **Renderizar/exportar** — concatenar, normalizar áudio, reenquadrar, exportar final | Sim, `ffmpeg` | Mesma condição do nível 3 |

**Sem o arquivo de vídeo em disco e sem autorização, a entrega para no briefing de edição.** É
isso que se diz ao cliente — não se promete corte que não vai acontecer.

Nenhum nível inclui: edição com julgamento estético (ritmo sentido, escolha de trilha, correção de
cor), inserção de B-roll que não existe, ou decisão de quais partes são "as boas" sem o roteiro em
mãos. Isso continua sendo trabalho humano.

### Regras de segurança do arquivo

1. **Preservar o original.** Nunca sobrescrever o bruto. Saída sempre em arquivo novo, em pasta
   separada.
2. **Testar em amostra antes do vídeo inteiro.** Processar 30-60 segundos, conferir áudio e
   sincronismo, só então rodar no arquivo completo. Render de 40 minutos com parâmetro errado é
   40 minutos perdidos duas vezes.
3. **Não cortar pausa que faz parte da demonstração, da respiração ou da execução segura.** O corte
   que "limpa" o silêncio de um procedimento faz parecer mais rápido e mais fácil do que é. Quem
   assiste vai tentar reproduzir.
4. **Conferir o corte contra o roteiro**, não só contra a transcrição — trecho que parece redundante
   no texto pode ser a recapitulação que o bloco seguinte precisa.
5. **Registrar o que foi cortado.** Lista de cortes aplicados junto do arquivo final, para
   auditoria e para regravar se algo ficou faltando.

## 4. Fluxo de edição na prática

```
bruto.mp4
  → transcrever  (mlx-whisper, pt, com timestamps)
  → ler contra o roteiro
  → lista de cortes com timecode + motivo de cada corte
  → [AUTORIZAÇÃO]
  → cortar amostra de 60s, conferir
  → cortar o vídeo inteiro (ffmpeg), original preservado
  → normalizar áudio / reenquadrar se necessário
  → checklist de revisão
```

## 5. Publicação e acessibilidade

- Legenda: subir a transcrição corrigida como legenda é barato e cobre quem assiste sem som. Vale
  como boa prática. O quanto isso muda retenção **em público específico** não é regra conhecida —
  um dado de terceiro não verificado sugere que o uso de legenda cai bastante em faixas mais
  velhas. [HIPÓTESE — testar no próprio canal]
- Descrição: primeira linha repete a promessa do título com as palavras do público; o resto
  contextualiza. Título, descrição e playlist são o que a busca cruza com a query.
  [OFICIAL — *Search & discovery tips*]
- Playlist por tema funciona como estrutura de descoberta em série. [RELATO — Derral Eves, via
  resumo de terceiro]
- Tag pesa pouco; excesso atrapalha mais do que ajuda. [RELATO — TubeBuddy]
