# Países da América do Sul

Sistema web acadêmico em **PHP + MySQL + HTML5 + CSS3** para cadastrar, consultar, editar e excluir informações sobre os países da América do Sul, incluindo **upload da bandeira**.

## Funcionalidades

- CRUD completo de países.
- Upload de bandeiras em PNG, JPG/JPEG ou WEBP (até 2 MB).
- Pesquisa de país pelo nome.
- Ordenação A→Z / Z→A.
- Total de países cadastrados.
- Página de detalhes.
- Mapa com Leaflet quando latitude e longitude estão cadastradas.
- Layout responsivo, cards, sombras, bordas arredondadas e efeitos hover.
- Banco inicial com os 12 países da América do Sul.
- Proteções básicas contra SQL Injection, XSS, CSRF e uploads inválidos.

## Requisitos

- PHP 8.1+ com extensões `pdo_mysql` e `fileinfo`.
- MySQL 8+ ou MariaDB compatível.
- Apache/Nginx. Para uso escolar, o XAMPP é suficiente.

## Instalação no XAMPP

1. Clone ou copie este projeto para a pasta `htdocs` do XAMPP. Exemplo:

   ```text
   C:\xampp\htdocs\Paises-da-America-do-sul
   ```

2. Inicie **Apache** e **MySQL** no painel do XAMPP.
3. Abra o phpMyAdmin (`http://localhost/phpmyadmin`).
4. Importe o arquivo `banco/america_sul.sql`.
5. Acesse:

   ```text
   http://localhost/Paises-da-America-do-sul/
   ```

Por padrão, o projeto usa as credenciais comuns do XAMPP:

```text
DB_HOST=127.0.0.1
DB_PORT=3306
DB_NAME=america_sul
DB_USER=root
DB_PASS=(vazio)
```

Se seu ambiente for diferente, configure essas variáveis no servidor antes de iniciar a aplicação.

## Estrutura do projeto

```text
Paises-da-America-do-sul/
├── banco/
│   └── america_sul.sql
├── css/
│   └── estilo.css
├── includes/
│   ├── footer.php
│   ├── form_pais.php
│   ├── functions.php
│   ├── header.php
│   └── init.php
├── tests/
│   └── functions_test.php
├── uploads/
│   └── .gitkeep
├── atualizar_pais.php
├── cadastrar_pais.php
├── conexao.php
├── detalhes.php
├── editar_pais.php
├── excluir_pais.php
├── index.php
├── listar_paises.php
├── menu.php
└── salvar_pais.php
```

## Testes e verificação

Executar os testes de funções:

```bash
php tests/functions_test.php
```

Verificar sintaxe de todos os arquivos PHP (Linux/macOS/Git Bash):

```bash
find . -name '*.php' -print0 | xargs -0 -n1 php -l
```

No Windows PowerShell:

```powershell
Get-ChildItem -Recurse -Filter *.php | ForEach-Object { php -l $_.FullName }
```

## Segurança implementada

- Consultas SQL com PDO e parâmetros preparados.
- Escape de saída HTML com `htmlspecialchars`.
- Token CSRF para cadastro, edição e exclusão.
- Exclusão somente via `POST`.
- Upload com limite de tamanho, validação MIME via Fileinfo, validação de imagem e nome aleatório.
- Mensagens de erro do banco não são exibidas ao usuário.
- Credenciais podem ser fornecidas por variáveis de ambiente.

## Observações

Os dados de presidente, população, IDH e PIB podem mudar com o tempo. O banco inicial deixa vários desses campos em branco para que sejam atualizados pelo próprio sistema. A Argentina contém o registro de exemplo fornecido na atividade.

O mapa utiliza Leaflet 1.9.4 e tiles do OpenStreetMap, portanto precisa de internet para carregar o mapa-base.
