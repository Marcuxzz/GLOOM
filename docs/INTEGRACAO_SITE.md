# Atualização automática do site (V7.3)

A partir da **versão V7.3 do site**, os botões de Windows e Android consultam automaticamente a **última Release estável pública** de [Marcuxzz/GLOOM](https://github.com/Marcuxzz/GLOOM/releases/latest). O site também mostra automaticamente a tag, como `v1.0.1`.

**Depois de publicar o site V7.3 no Cloudflare Pages uma vez, não é necessário modificar os links nem republicar o HTML para atualizar somente o jogo.**

Como publicar versões seguintes:

1. Compile o jogo no GameMaker e teste as compilações.
2. Crie uma **nova Release pública estável** com uma nova tag (`v1.0.1`, `v1.0.2` etc.) em https://github.com/Marcuxzz/GLOOM/releases/new.
3. Anexe **os dois arquivos exatamente com estes nomes**: `GLOOM-Windows.zip` e `GLOOM-Android.apk`.
4. Publique a Release. Na próxima visita/recarga, o site consultará o GitHub e atualizará versão e links automaticamente (com pequeno atraso possível de cache).

Se uma plataforma não tiver arquivo na Release mais recente, o botão ficará indisponível até que seja anexado. O link estável de reserva é `https://github.com/Marcuxzz/GLOOM/releases/latest/download/<nome-do-arquivo>`.

As versões anteriores do site (até V7.2) continuam usando links salvos em Supabase; as instruções a seguir permanecem úteis apenas para essas versões ou para links alternativos.

---

# Conectar os downloads ao site GLOOM

O site oficial do GLOOM usa Cloudflare Pages para os arquivos estáticos e Supabase para administrar postagens e links de download.

## Requisitos

No Supabase, a tabela `public.gloom_downloads` precisa estar criada com duas linhas:

- `pc`
- `android`

O administrador precisa estar cadastrado em `public.gloom_admins`. As regras RLS devem permitir leitura pública e gravação somente aos administradores.

## Como cadastrar os links

1. Publique os instaladores em uma release pública, conforme [PUBLICACAO.md](PUBLICACAO.md).
2. Abra o site do GLOOM e entre em **CRIADOR**.
3. Localize **VERSÕES PARA DOWNLOAD**.
4. Informe o URL HTTPS de cada asset e seu número de versão.
5. Salve em **ATUALIZAR DOWNLOADS**.
6. Abra uma janela anônima e teste os downloads.

É possível usar links diretos de uma tag específica:

```text
https://github.com/Marcuxzz/GLOOM/releases/download/v0.1.0/GLOOM-Windows.zip
https://github.com/Marcuxzz/GLOOM/releases/download/v0.1.0/GLOOM-Android.apk
```

Ou os links estáveis de versão final:

```text
https://github.com/Marcuxzz/GLOOM/releases/latest/download/GLOOM-Windows.zip
https://github.com/Marcuxzz/GLOOM/releases/latest/download/GLOOM-Android.apk
```

**Importante:** URLs acima são modelos e retornam erro até a primeira release conter os arquivos.

## Verificar os links no Supabase

Execute no SQL Editor:

```sql
select platform, url, version, updated_at
from public.gloom_downloads
order by platform;
```

A atualização dos links via painel é independente do deploy do Cloudflare. Se os botões continuarem desativados, confira o SQL de downloads, a autenticação de administrador e os URLs salvos.

## A publicação pelo GameMaker é automática?

Não com a configuração atual. O GameMaker gera builds locais. Publicá-las automaticamente no GitHub exigiria configurar uma pipeline externa com um runner GameMaker autorizado, acesso às ferramentas de compilação e credenciais protegidas. O procedimento manual por release é o primeiro caminho seguro e verificável.

## Atualização do aplicativo instalado

Alterar o link no site **não atualiza automaticamente** instalações antigas de Windows ou Android. Isso exigiria um mecanismo de atualização próprio ou distribuição por uma loja que cuide das atualizações.
