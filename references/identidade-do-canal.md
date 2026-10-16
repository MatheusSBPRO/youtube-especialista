# Identidade do canal

Monte tudo como pacote, mostre ao expert e só aplique no Studio depois do ok. Antes de trocar,
salve o estado atual: os arquivos de banner e foto, a descrição, os links, as playlists e prints da
página inicial. Assim dá para voltar atrás.

## Banner (2560×1440)

- **Área segura:** 1546×423 no centro. É o que aparece no celular. Título, frase e rosto ficam dentro
  dela.
- **Texto:** o posicionamento nas palavras do próprio expert. Tire uma frase literal de um vídeo
  dele, e não um slogan inventado. Uma linha grande (o que ele entrega) e uma pequena (o que a vida
  da pessoa ganha).
- **Foto:** real, de um frame bom de vídeo ou de um ensaio. **Nada de IA no rosto.** Para recortar o
  fundo, use segmentação que só gera a máscara.
- **No banner não entram:** promessa de resultado, credencial que o expert não falou em vídeo, nem
  dia de postagem que ainda não é fixo.
- **Prévia antes de subir:** recorte celular (1546×423), simulação a 390 px de largura, desktop
  (2560×423) e TV (inteiro). Olhe as quatro.
- **Atenção:** câmera frontal espelha. Texto de camiseta invertido entrega o espelhamento, então
  corrija com hflip antes.

## Foto de perfil (800×800)

- **Teste a 98 px**, o tamanho em que ela aparece ao lado do comentário. O rosto tem que ser
  reconhecível nesse tamanho.
- **Enquadramento:** do peito para cima, de frente, olhando para a câmera. O rosto ocupa metade da
  altura, com espaço acima da cabeça, porque o YouTube corta em círculo.
- **Fundo:** liso, sem nada atrás da cabeça. **Não use branco**, que some no tema claro. Uma cor da
  marca funciona bem.
- **Luz:** de janela, de frente, sem contraluz e sem filtro.
- **Envio:** peça o arquivo original, mandado como documento, porque foto pelo WhatsApp comprime.
- **Atualizada:** a pessoa que ele é hoje nos vídeos. Quem vê a miniatura e depois a foto tem que
  ligar uma à outra.
- **Conta pessoal:** se o canal estiver ligado à conta Google pessoal do expert, trocar a foto troca
  também a do Gmail dele. Confira antes.

## Descrição do canal (até 1.000 caracteres, em 1ª pessoa)

1. **A 1ª frase diz o que o canal entrega e para quem**, com as palavras que o público busca.
2. **A credencial é só a que o expert disse em vídeo** ou deixou por escrito. Nada de inventar número
   de alunos nem de anos.
3. **A promessa do canal**, também na fala dele ("aqui eu trago um teste para você fazer em casa e o
   que fazer depois").
4. A frase-assinatura dele, se tiver.
5. Se o assunto é saúde ou dinheiro, o aviso: "informação geral, não substitui o profissional que
   te acompanha".

**Sem URL na descrição.** Os links ficam na seção de links, logo abaixo.

## Links do canal

| Ordem | O quê | Observação |
|---|---|---|
| 1º | O destino da palavra que está rodando (captação ou produto) | É o que aparece no topo do canal, ao lado do nome. É o link que quem vem do Short clica |
| 2º | O segundo produto, ou a isca | — |
| 3º | Instagram do expert | — |

- O título de cada link tem até 30 caracteres.
- Todos são diretos, com `utm_source=youtube&utm_medium=organico&utm_content=canal-links`.
- Abra cada link antes de salvar. Ele tem que responder, a página tem que ser a certa e o checkout,
  o real.
- Fora: rede social sem uso, site que não abre, e produto de outro público (ex.: um curso para
  profissionais num canal para o consumidor final).

## Playlists

São de 3 a 4, em ordem manual, cada uma com uma promessa. Por exemplo:

1. "Comece por aqui": o melhor vídeo de entrada e os testes ou diagnósticos.
2. "Por que [o problema] acontece": a explicação.
3. "Histórias de alunos": a prova.
4. "Dúvidas de quem vai começar": as objeções.

O Short de bastidor, de chamada de venda ou de outro público fica fora das playlists novas. As
playlists antigas continuam no canal e só saem da página inicial.

## Página inicial

- **Trailer para quem não é inscrito:** o melhor vídeo longo de entrada. Enquanto não houver um bom,
  deixe sem trailer. Vídeo antigo fora de contexto não serve.
- **Destaque para quem já é inscrito:** o longo mais novo. A troca é manual, a cada publicação.
- **Seções:** "Comece por aqui", Shorts, e as outras playlists.
- **A prateleira "Vídeos"** só volta quando houver 3 longos novos. Antes disso, ela mostra o vídeo
  velho logo abaixo do novo.
- **Vídeo antigo:** não apague, porque perde histórico e visualizações. Tornar não listado é decisão
  do expert.

## Marca d'água (150×150, PNG transparente)

- É a foto de perfil num círculo com borda clara, para destacar em vídeo escuro e em vídeo claro.
- Aparece no vídeo inteiro. No computador, ela vira botão de inscrição. Nos Shorts não aparece.
- Trocou a foto, refaça a marca d'água.

## Padrões de upload (Configurações › Padrões de upload)

O padrão vale para tudo que sobe pelo Studio, inclusive os Shorts do robô. O `subir.mjs` apaga a
descrição antes de escrever a dele, então o rodapé padrão não entra nos Shorts.

| Campo | Valor |
|---|---|
| Título | vazio |
| Descrição | o rodapé (apresentação curta do expert, link da playlist "Comece por aqui", Instagram e aviso, se for saúde ou dinheiro). **Sem link de produto.** Ele entra vídeo a vídeo, quando combina com o assunto |
| Visibilidade | Privado (nada vai a público por engano) |
| Tags | o nome do expert e 8 a 10 termos que o público busca |
| Categoria | Instrução e estilo, ou Educação |
| Idioma | Português (Brasil), no vídeo e no título |
| Comentários | ativados, com "reter potencialmente inapropriados" (nunca "reter todos") |
| Publicar no feed de inscrições e notificar | sim |
| Conteúdo alterado ou sintético | é por vídeo, e não no padrão. Teve cena de IA, marque "sim" |

**Palavras-chave do canal** (Configurações › Canal): o nome do expert, os produtos e os termos de
busca do nicho. O peso na descoberta é pequeno. O que manda é o título, a miniatura e o
comportamento de quem assiste. [OFICIAL: YouTube Help]

## Checklist de aplicação no Studio

- [ ] O expert deu o ok em banner, foto, descrição e links (por escrito).
- [ ] O estado atual está salvo.
- [ ] Banner e foto trocados. A marca d'água foi refeita, se a foto mudou.
- [ ] Descrição colada. A contagem de caracteres cabe em 1.000.
- [ ] Links em ordem, e cada um aberto e conferido.
- [ ] Playlists criadas, em ordem manual e públicas.
- [ ] Página inicial com trailer, destaque e seções.
- [ ] Padrões de upload salvos. O link da playlist entrou no rodapé.
- [ ] O público do canal está em "não é para crianças".
- [ ] Conferido sem login (janela anônima): o canal aparece como o expert queria.
