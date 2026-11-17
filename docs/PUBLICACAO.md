# Publicar uma versão do GLOOM

Este repositório é **somente para distribuição pública** do jogo, sem o projeto-fonte do GameMaker.

## 1. Exportar os arquivos

No GameMaker, gere e teste as duas versões:

- Windows: pasta de build empacotada como `GLOOM-Windows.zip`. Inclua os arquivos necessários para executar o jogo, não apenas um executável isolado se a compilação exigir dependências.
- Android: `GLOOM-Android.apk`, assinado com sua chave de publicação. **Nunca coloque a chave de assinatura ou suas senhas neste repositório.**

Teste o ZIP em outro computador Windows e o APK em um Android de teste antes de publicar. Se houver versão sem uma das plataformas, publique apenas a versão existente.

## 2. Criar uma GitHub Release

1. Acesse https://github.com/Marcuxzz/GLOOM/releases/new
2. Em **Choose a tag**, crie uma tag de versão, por exemplo `v0.1.0`.
3. No título, informe `GLOOM v0.1.0`.
4. Descreva o que mudou, recursos conhecidos, requisitos e avisos.
5. Anexe `GLOOM-Windows.zip` e/ou `GLOOM-Android.apk` em **Assets**.
6. Use **Set as a pre-release** se for uma versão de testes.
7. Clique em **Publish release**.

Não publique uma release vazia: os botões de download precisam de arquivos reais.

## 3. Links estáveis para o site

Estes endereços apontam para o arquivo com esse nome na release mais recente:

- Windows: https://github.com/Marcuxzz/GLOOM/releases/latest/download/GLOOM-Windows.zip
- Android: https://github.com/Marcuxzz/GLOOM/releases/latest/download/GLOOM-Android.apk

Os links só funcionam após uma release pública válida com os nomes exatos. Se você usar uma prévia (pre-release), o caminho `latest` pode não selecioná-la. Para testes, copie o link direto do asset dessa release.

## 4. Atualizações futuras

Para a versão seguinte, por exemplo `v0.1.1`:

1. Compile e teste novamente no GameMaker.
2. Crie uma **nova release** com a nova tag.
3. Anexe arquivos com os **mesmos nomes**.
4. Publique a release.

Desse modo, os links `releases/latest/download/...` podem continuar os mesmos entre versões finais; confirme se a última release selecionada realmente contém ambos os arquivos.

## Segurança

- Não envie os arquivos `.yyp`, `.gml`, recursos internos de edição, keystore Android, tokens ou credenciais.
- Não coloque configurações privadas do Supabase no GitHub.
- Verifique o conteúdo do ZIP antes de publicar.
- Os instaladores são públicos: qualquer pessoa com o link poderá baixá-los.
- A publicação da release exige uma ação no GitHub; este repositório não compila automaticamente o GameMaker.
