# Método de plataforma — distribuição, métricas e leitura de resultado

O que não dá para inferir olhando o vídeo. Marcações de origem em `fontes-pesquisadas.md`.

## 1. Como a distribuição funciona (até onde é público)

- O sistema combina **dois grupos de sinal**: personalização do espectador (histórico, afinidade) e
  desempenho do conteúdo (clique, tempo assistido, pesquisas de satisfação pós-visualização). CTR
  isolado nunca é o critério inteiro. [OFICIAL — *Recommendation System*]
- A busca ranqueia por **relevância + engajamento + qualidade**, cruzando a query com título,
  descrição, tags e conteúdo. O YouTube afirma que não vende posição de busca. [OFICIAL — *Search &
  discovery tips*]
- **Concorrência e sazonalidade** mudam o alcance e não aparecem como métrica no Studio. Dois
  vídeos iguais podem performar diferente sem causa visível: o seu pode ter perdido o espectador
  para outro vídeo, e você nunca vai ver isso em lugar nenhum. [OFICIAL — *Search & discovery tips*]
- A recomendação é **por vídeo**, não por canal — canal grande não tem prioridade estrutural.
  [RELATO — TubeBuddy]
- Canal novo é testado por **comportamento** (tempo assistido, CTR), não por contagem de inscrito.
  Canal zerado não está em desvantagem estrutural. [RELATO — TubeBuddy]
- Nenhuma fonte, nem a oficial, detalha **por que um vídeo específico foi ou não recomendado**.
  Qualquer explicação categórica sobre isso é chute. [OFICIAL, por ausência]

## 2. Métricas que importam, e como ler cada uma

| Métrica | Lê o quê | Armadilha |
|---|---|---|
| Impressões | Quanto o YouTube está oferecendo o vídeo | Travado em zero = não está saindo de quem já segue o canal [RELATO — TubeBuddy] |
| CTR | Força da embalagem | Só comparável **dentro da mesma origem** (Busca ≠ Browse ≠ Sugeridos ≠ Notificação) |
| Duração média / % assistido | Entrega x promessa | O número importa menos que **onde** o espectador some no gráfico |
| Novos / casuais / regulares | Saúde da comunidade | "Regular" (6+ meses no ano) é o proxy de fã; substituiu o "recorrente" binário [OFICIAL] |
| Tempo de exibição total | Volume | Cresce só por postar mais — nunca ler isolado |
| Origem de tráfego | Como o vídeo está sendo achado | Browse costuma aparecer **depois** que CTR e retenção provaram o vídeo num público menor [RELATO — TubeBuddy] |

Faixa de referência para canal pequeno (<1.000 inscritos): CTR 4-10%, retenção 35-50% já acima da
média (~23,7%). [RELATO — TubeBuddy, blog de ferramenta paga] Tratar como **ordem de grandeza**,
nunca como meta contratual com cliente.

Shorts e vídeo longo não são comparáveis em retenção: Short é curto e em loop, o número infla por
formato, não por qualidade. [RELATO — vidIQ, fonte fraca — só snippet de busca, fetch retornou 429]

## 3. Janela de leitura

| Quando | O que checar | Decisão possível |
|---|---|---|
| ~1 hora | Impressões subiram? | Se zero, checar se publicou como deveria (visibilidade, agendamento) |
| 6-12 horas | CTR e retenção inicial | É o que decide se o teste é ampliado |
| 24 horas | Apareceu Browse Features? | Se não, o vídeo ficou no público que já segue |
| Semanas/meses | Busca e sugeridos | Evergreen ressuscita — não decretar fracasso em 48h [RELATO — TubeBuddy] |

Diagnóstico cruzado, o mais útil da tabela toda:

| CTR | Retenção | Leitura | Ação |
|---|---|---|---|
| Baixo | Alta | Embalagem não vendeu um vídeo bom | Retestar título/thumb no vídeo já publicado [RELATO — Ed Lawrence] |
| Alto | Baixa | Clickbait quebrado: prometeu o que não entregou | Corrigir promessa, não dobrar a aposta [RELATO — TubeBuddy] |
| Baixo | Baixa | Ou o tema não interessa, ou o público está errado | Voltar à etapa 2, não à edição |
| Alto | Alta | Funcionou | Perguntar o que exatamente, e repetir a estrutura — não o tema |

## 4. Armadilhas de interpretação

- **Correlação não é causa.** O Studio mostra o que aconteceu, não a decisão do algoritmo. Não dá
  para saber se foi o título, o horário, a concorrência ou a sazonalidade. [OFICIAL]
- **Viral ≠ canal saudável.** Pico traz espectador fora do perfil e derruba a retenção média dos
  próximos vídeos sem que nada tenha piorado na produção. [RELATO — TubeBuddy]
- **Vídeo único em canal pequeno é ruído.** CTR e demografia de um vídeo isolado têm amostra
  pequena demais. Olhar a tendência de vários vídeos. [RELATO — TubeBuddy]
- **Inscrito oscila por dia.** Ler variação semanal. [RELATO — TubeBuddy]
- **Tag não é truque.** Pesa pouco frente a título e descrição; excesso atrapalha. [RELATO — TubeBuddy]
- **Postar todo dia não é o fator.** Consistência que o criador aguenta manter pesa mais.
  [RELATO — TubeBuddy]
- **A armadilha central:** transformar relato de criador em regra confirmada do algoritmo. Mesmo os
  profissionais mais citados falam de prática, não de mecanismo interno.

## 5. O que não está confirmado (não usar como regra)

- Mecânica interna do algoritmo de Shorts em 2026 ("sistema de 3 portões", limiar exato de
  swipe-through). Aparece repetida em agregadores de SEO, nenhuma confirmação oficial ou de fonte
  nomeada. [HIPÓTESE]
- "Session contribution como sinal líder" e o suposto overhaul do Browse feed em fevereiro/2026.
  A parte de satisfação bate com a documentação oficial; a parte específica, não. [HIPÓTESE]
- Legenda como fator decisivo de retenção para público mais velho: há um dado de terceiro, não
  verificado, de que o uso de legenda cai muito nas faixas acima de 55 anos. Testar no próprio
  canal antes de tratar como regra. [HIPÓTESE]

## 6. Leitura sem acesso ao Analytics

Quem gerencia o canal como Administrador pelo Studio não usa a API do YouTube Analytics (ela pede o
login do dono). O `scripts/analise/coletar.mjs` lê a análise direto do Studio. Sem nenhum acesso:

1. Pedir ao cliente o export CSV ou prints das telas: visão geral, retenção do vídeo, origens de
   tráfego, CTR por origem.
2. Registrar na análise que a leitura é parcial e qual tela faltou.
3. Nunca estimar número que não foi visto. Campo sem dado é campo vazio com a lacuna nomeada.
