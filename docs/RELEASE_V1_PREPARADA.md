# GLOOM — Arquivos selecionados para primeira Release

**Status:** compilações selecionadas e verificadas localmente; **ainda não enviadas como assets do GitHub Releases**.

## Distribuição escolhida

| Plataforma | Nome do arquivo na Release | Tamanho | Observação |
|---|---|---:|---|
| Windows x64 | `GLOOM-Windows.zip` | 5.264.677 bytes | Inclui `GLOOM.exe` (x64), `data.win` e `options.ini` |
| Android | `GLOOM-Android.apk` | 20.523.442 bytes | APK com suporte ARM64, assinado; opção GameMaker `Debug=False` |

O `GLOOM.exe` separado enviado pelo desenvolvedor foi identificado como instalador NSIS, mas ficou fora da distribuição principal para evitar duas alternativas de Windows sem teste funcional do instalador.

O APK informa versão `1.0.0` no arquivo de opções. O número da primeira tag proposto é `v1.0.0`; ainda precisa ser confirmado como a versão que se deseja divulgar.

### SHA-256 dos arquivos preparados

```text
9259ad8e5e82423d832b2c1fc5867e3410b472c5f9b17f85d30ec1b1ecbc004d  GLOOM-Windows.zip
93213df41f287925dcfa9a566bf7dcd82d606259c4183b60696aa414dc2be149  GLOOM-Android.apk
```

**Validação realizada:** CRC e estrutura dos dois pacotes ZIP/APK conferidos; assinatura Jar do APK verificada com `jarsigner`. **Não há verificação funcional em Windows ou em Android.** O certificado do APK é autoassinado, prática comum em instalações fora de lojas, mas isso não elimina alertas de segurança que possam aparecer no dispositivo.

## Publicação dos executáveis

Para criar a primeira Release: https://github.com/Marcuxzz/GLOOM/releases/new

1. Selecione a tag `v1.0.0` (ou a versão final correspondente).
2. Cole o conteúdo de [MODELO_RELEASE.md](MODELO_RELEASE.md) adaptado à versão.
3. Anexe os dois arquivos listados na tabela.
4. Publique a Release e confira os downloads.

Após a publicação, o site do GLOOM pode apontar para:

- https://github.com/Marcuxzz/GLOOM/releases/latest/download/GLOOM-Windows.zip
- https://github.com/Marcuxzz/GLOOM/releases/latest/download/GLOOM-Android.apk

Esses endereços **não funcionam enquanto a Release não contiver os arquivos**.

Não envie projeto-fonte `.yyp`/`.gml` ou credenciais para este repositório público.
