# NEXUM by Tigre — site institucional

Arquivos estáticos do site público. Este repositório contém apenas a vitrine:
nenhum código da engine, nenhuma peça, nenhum dado de processo.

## Publicação

GitHub Pages, a partir da branch `main`, pasta raiz (`/`).
Settings → Pages → Build and deployment → Deploy from a branch.

## Domínio

Domínio canônico: **`ribeiroetigre.org`** (ápice). `canonical`, `og:url`,
`sitemap.xml` e `robots.txt` apontam para ele. O arquivo `CNAME` na raiz
instrui o GitHub Pages a servir o domínio próprio e a emitir o certificado.

Espelho secundário: `https://martbarreto-sudo.github.io/supreme-drafter-landing/`
(com o `CNAME` presente, o GitHub redireciona o espelho para o domínio próprio).

### Registros DNS (zona `ribeiroetigre.org`)

| Nome | Tipo | Valor | Proxy Cloudflare |
|---|---|---|---|
| `@` | A | `185.199.108.153` | desligado (DNS only) |
| `@` | A | `185.199.109.153` | desligado |
| `@` | A | `185.199.110.153` | desligado |
| `@` | A | `185.199.111.153` | desligado |
| `www` | CNAME | `martbarreto-sudo.github.io` | desligado |

Proxy desligado durante a emissão do certificado (o GitHub valida o domínio
por HTTP). Depois de "Enforce HTTPS" ativo no GitHub, o proxy pode ser ligado
com SSL/TLS em modo **Full (strict)**; em modo **Flexible** o site entra em
laço de redirecionamento.

### Ordem do cutover

1. Remover da zona qualquer registro `@`/`www` anterior (origem antiga).
2. Criar os registros da tabela acima.
3. Mesclar o PR que adiciona o `CNAME` (este arquivo só entra em `main`
   junto com o DNS, senão o espelho `github.io` passa a redirecionar para
   um domínio que ainda não responde).
4. GitHub → Settings → Pages: confirmar "Custom domain = ribeiroetigre.org",
   aguardar "DNS check successful", marcar "Enforce HTTPS".
5. Conferir: `https://ribeiroetigre.org/` (200), `https://www.ribeiroetigre.org/`
   (301 para o ápice), `https://ribeiroetigre.org/sitemap.xml`.

## Contato

Os botões de acesso à sessão e de contato com a banca apontam para
`contato@ribeiroetigre.adv.br`. Não há portal de equipe publicado neste
domínio; quando houver (`app.*` sob Cloudflare Access), trocar os `mailto:`
pelo endereço do portal.

## Regra

Só entram aqui arquivos estáticos do site. Peças, números de processo, nomes
de partes e credenciais nunca são versionados neste repositório.
