---
name: transcrever
description: >
  Baixa a transcrição de um vídeo do YouTube e salva em estudos/.
  Extrai os pontos principais e gera um resumo de estudo.
  Use quando o usuário colar um link do YouTube e quiser transcrever,
  estudar o conteúdo ou usar como base pra criar conteúdo.
---

# /transcrever — Transcrição de Vídeo do YouTube

## Dependências

- **yt-dlp:** `C:/Users/WIN-10/yt-dlp.exe` — instalado localmente
- **Contexto:** `_contexto/empresa.md` e `_contexto/preferencias.md`

---

## Workflow

### Passo 1 — Receber o link

O usuário fornece o link do vídeo do YouTube.

Se não forneceu, perguntar: "Me passa o link do vídeo do YouTube."

### Passo 2 — Baixar a transcrição

Rodar o comando pra baixar a legenda/transcrição do vídeo:

```bash
C:/Users/WIN-10/yt-dlp.exe --write-auto-sub --sub-lang pt,en --skip-download --output "estudos/%(title)s" "[URL]"
```

Se o vídeo não tiver legenda em português, tentar em inglês.

Se não tiver nenhuma legenda automática disponível, informar:
> "Esse vídeo não tem legenda disponível. Quer que eu tente outra abordagem ou passa outro link?"

### Passo 3 — Processar o texto

Após baixar, ler o arquivo de legenda gerado e:
1. Limpar o texto (remover timestamps, tags, repetições)
2. Identificar o título do vídeo

### Passo 4 — Gerar o estudo

Com o texto limpo, gerar um documento de estudo com:

```markdown
# [Título do vídeo]

**Fonte:** [URL]
**Data:** [data de hoje]

---

## Resumo

[3-5 frases com a ideia central do vídeo]

## Pontos principais

[Lista dos insights mais importantes — em linguagem direta, sem copiar o texto original]

## Citações relevantes

[Trechos que valem guardar literalmente]

## Ideias de conteúdo

[2-3 ângulos pra transformar isso em carrossel, reel ou post — baseado no perfil MIGO FLOW / comerciantes locais]
```

### Passo 5 — Salvar

Salvar em `estudos/[slug-do-titulo]-[data].md`

Confirmar:
> "Transcrição feita. Salvo em estudos/[nome-do-arquivo].md
> Quer usar isso pra criar um carrossel ou roteiro agora?"

---

## Regras

- Tom das anotações: direto e informal, igual às preferências do Robson
- Sempre sugerir ângulos de conteúdo no final — o objetivo não é só estudar, é também produzir
- Se o vídeo for longo (+30min), focar nos pontos mais aplicáveis pro público de comerciantes locais
- Não resumir de forma genérica — filtrar pelo que é relevante pro negócio local e SaaS
