# 🧱 Projeto Symfony com PHP 8, Nginx e MySQL 8

Este é um projeto baseado no framework **Symfony**, desenvolvido em **PHP 8**, utilizando **Nginx** como servidor web e **MySQL 8** como banco de dados.

---

## 🧰 Tecnologias Utilizadas

- ✅ PHP 8
- ✅ Symfony Framework
- ✅ MySQL 8
- ✅ Nginx
- ✅ Composer

---

## ⚙️ Pré-requisitos

Certifique-se de ter os seguintes softwares instalados em seu ambiente:

- PHP 8.x com as extensões:
  - `pdo`, `mbstring`, `xml`, `intl`, `openssl`, `curl`, `zip`, `gd`
- Composer (https://getcomposer.org/)
- MySQL 8
- Nginx
- Symfony CLI (opcional, mas recomendado)

---

## 🚀 Instalação

1. **Clone o repositório**

```bash
git clone https://github.com/seu-usuario/seu-projeto.git
cd seu-projeto
```

2. **Instale as dependências do PHP**
```
composer install
```

3. **Configure as variáveis de ambiente**

Crie ou edite o arquivo `.env`:
```
DATABASE_URL="mysql://usuario:senha@127.0.0.1:3306/nome_do_banco"
```

4. **Crie o banco de dados e execute as migrations**
```
php bin/console doctrine:database:create
php bin/console doctrine:migrations:migrate
```

## ▶️ Execução

**Usando Symfony CLI**
```
symfony serve
```

**Usando servidor embutido do PHP**
```
php -S 127.0.0.1:8000 -t public
```
**Usando Nginx**

Exemplo de configuração Nginx `(/etc/nginx/sites-available/symfony.conf)`:
```
server {
    listen 80;
    server_name localhost;
    root /caminho/para/seu-projeto/public;

    location / {
        try_files $uri /index.php$is_args$args;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~ /\.ht {
        deny all;
    }
}
```

Ativando a configuração:

```
sudo ln -s /etc/nginx/sites-available/symfony.conf /etc/nginx/sites-enabled/
sudo systemctl reload nginx
```

## 📁 Estrutura do Projeto Symfony

`src/` – Código-fonte da aplicação

`config/` – Arquivos de configuração

`templates/` – Templates Twig

`public/` – Diretório público (raiz da aplicação)

`migrations/` – Migrations do banco de dados

`.env` – Variáveis de ambiente

## 🔧 Comandos Úteis do Symfony
```
php bin/console cache:clear       # Limpar o cache
php bin/console debug:router      # Ver rotas registradas
php bin/console make:controller   # Criar um novo controller
php bin/console doctrine:schema:update --force  # Atualizar schema do banco
```

## 📜 Licença
Este projeto está licenciado sob a [MIT License](https://mit-license.org/).
