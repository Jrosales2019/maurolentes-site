# maurolentes-site

Site das Oticas Mauro Lentes (maurolentes.com.br), hospedado no servidor PEDRO.
O Jhoni (sysadmin da Plugweb) pede mudancas pelo celular, com print e descricao. Responda em portugues do Brasil, curto e direto.

## Onde esta a verdade
O site publicado e a fonte da verdade: `C:\Inetpub\vhosts\maurolentes.com.br\httpdocs` no PEDRO (Windows Server 2019, Plesk, IIS).
Nao ha codigo-fonte nem build: so arquivos prontos (`index.html`, `assets/index-*.js` minificado, `assets/index-*.css`, `images/`).
Este repositorio guarda so o mapa, a skill `atualizar-site` e o historico (`HISTORICO.md`). Nao copie o site para ca.

## Regras
1. Nenhum comando roda no servidor sem ser mostrado inteiro no chat antes, com veredito, e sem o ok do Jhoni (cartao AskUserQuestion).
2. Todo script de mudanca faz copia de seguranca do site antes de alterar (pasta `_backups` fora de `httpdocs`).
3. Troca de texto: o texto antigo precisa aparecer exatamente 1 vez; senao o script para sem mexer.
4. Resultado volta pelo relatorio no Drive, que voce le e mostra literal.
5. Nao mexer em DNS, e-mail, MailEnable nem em outros dominios. Nao ler `AUTH.TAB`, `Postoffices` nem corpo de e-mail.
6. Cada mudanca feita entra em `HISTORICO.md` (data, o que mudou, backup usado).
7. Imagem nova: o Jhoni coloca no Drive (`PlugWork/Claude/maurolentes.com.br`); o script copia para `httpdocs\images`. Nunca passe imagem pelo contexto.

## Servidor (descoberto em 25/10/2026)
- Dominio no Plesk: `maurolentes.com.br`, hospedagem fisica, IP 162.214.152.121, www-root `httpdocs`, usuario FTP `maurolentes` (senha aleatoria, desconhecida).
- `plesk.exe`: `C:\Program Files (x86)\Plesk\bin\plesk.exe`. Comandos de dominio: `plesk bin domain --update`; leitura: `plesk bin site --info`.
- URL Rewrite instalado; `web.config` do site faz rota unica para `/index.html`. O site forca HTTPS (HTTP responde 301).
- Teste pelo servidor: HttpWebRequest com `Host: maurolentes.com.br` em 127.0.0.1, HTTPS com callback de certificado.
- Site atual: Vite/React ja compilado, 42 arquivos (39 jpg), `index.html` na raiz.
- Node do servidor e 18: nao compila nada novo; nao ha necessidade.

## Canal de publicacao (PowerShell 5.1, so ASCII)
Drive, pasta mestre `Scripts\Vigilancia` (id `17cXTpKrEUlyq5gAkLTiOHVMtlr_6iScU`): `Publicar.ps1` + `manifesto.json` (SHA-256).
O Atualizador (1 min, conta do Jhoni) roda o `Publicar.ps1` uma vez e grava `Relatorios\resposta-canal-*.txt`.
Passo a passo completo e modelo de relatorio: skill `atualizar-site`.
