---
name: atualizar-site
description: Atualiza o site maurolentes.com.br direto no servidor PEDRO (texto, imagem, links) a partir de print e descricao do Jhoni. Use quando ele pedir qualquer mudanca no site.
---

# Atualizar o site Mauro Lentes

Fluxo, sempre nesta ordem:
1. **Entender** o pedido (print + descricao). Se faltar o texto exato, pergunte em 1 linha.
2. **Localizar** o trecho: script SOMENTE LEITURA que procura o texto em `httpdocs` (`index.html`, `assets\*.js`, `assets\*.css`) e relata arquivo, quantas vezes aparece e ~120 caracteres de contexto. Mostre o relatorio literal.
3. **Propor** o script de mudanca e mostra-lo INTEIRO, com veredito, antes de subir. Cartao: aprovar / nao aprovar / conversar.
4. **Script de mudanca** (`Publicar.ps1`, ASCII, PS 5.1):
   - copia SO os arquivos que vai alterar para `C:\Inetpub\vhosts\maurolentes.com.br\_backups\AAAAMMDD-HHMMSS` (a copia completa de base em zip e feita uma unica vez, na 1a mudanca) e apaga as pastas de backup mais antigas, mantendo as 10 ultimas;
   - para cada troca, confere que o texto antigo aparece exatamente 1 vez; se nao, PARA sem mexer;
   - grava UTF-8 sem BOM; imagem: copia de `G:\My Drive\PlugWork\Claude\maurolentes.com.br\<arquivo>` para `httpdocs\images\`;
   - testa `https://127.0.0.1/` com Host `maurolentes.com.br` (200, tamanho, texto novo presente);
   - grava o relatorio em `Relatorios\resposta-canal-*.txt`.
5. **Publicar** no Drive: `Publicar.ps1.novo`, `manifesto.json.novo` por ultimo, renomear, conferir bytes. Modelo e manifesto: seguir o fluxo do canal (gerar-manifesto: SHA-256 de todos os `.ps1` da pasta mestre, validade ate 120 min).
6. **Confirmar**: ler o relatorio (1 a 6 min), mostrar literal, dizer "no ar" so com o teste verde. Visual: o Jhoni confere no celular.
7. **Registrar** em `HISTORICO.md`.

Rollback: copiar de volta os arquivos da pasta de `_backups` da mudanca (ou o zip de base) para `httpdocs` (script proprio, mostrado antes).
Mudanca de layout/estrutura no JS minificado: avisar o risco antes e propor teste num arquivo copia.
