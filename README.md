# Vitrine — Frontend PHP

Interface de gestão da loja. O frontend envia as solicitações à API Node.js;
tokens de autenticação são mantidos apenas na sessão PHP.

## Requisitos

- PHP 8.1 ou superior, com as extensões `json` e `session`.
- API Simples disponível e configurada com acesso ao banco de dados.

## Executar localmente

Inicie a API na porta `5000`. Em outro terminal, inicie o servidor PHP:

```powershell
$env:API_BASE_URL = "http://127.0.0.1:5000"
php -S 127.0.0.1:8000 -t .
```

No Windows, se o PHP não estiver no `PATH`, substitua `php` pelo caminho para
`php.exe`. Abra `http://127.0.0.1:8000` e entre com uma conta existente.

Sem `API_BASE_URL`, o frontend usa `http://127.0.0.1:5000`. Em produção,
configure essa variável no ambiente PHP com a URL HTTPS da API. O arquivo
`.htaccess` também define a URL usada pelo Apache.

## Segurança

Não versionar arquivos `.env`, senhas, tokens ou outras credenciais. O
`.gitignore` exclui arquivos de ambiente locais. As sessões PHP usam cookies
`HttpOnly` e proteção CSRF nos formulários.
