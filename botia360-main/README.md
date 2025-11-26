# Botia360

Botia360 es una empresa distribuidora de White Label que posee una solución de atendimientos via Whatsapp que aumenta la productividad y organización de los equipos

## 🚀 Começando

El repositorio de Botia360 posee 3 carpetas importantes:
- backend
- frontend
- instalador

El backend es hecho en Express y posee toda la estructura organizada dentro de esa carpeta para que se pueda aplicar en el entorno del cliente. La carpeta de frontend contiene todo el framework del React.js que gestiona toda la interacción con el usuario del sistema.

La carpeta de instalador dentro de ese repositorio es una copia del instalador usado para que los clientes de sistemas puedan hacer el clone dentro de la carpeta home de sus servidores y seguir con la instalación automática de todas las dependencias del proyecto

Link para el repositorio del instalador actualizado:
- [Instalador](https://github.com/atendechat-org/instalador)

Consulte **[Implantação](#-implanta%C3%A7%C3%A3o)** para saber como implantar el proyecto.

### 📋 Pré-requisitos

```
- Node.js v20.x
- Postgres (release)
- Npm ( latest )
- Docker (bionic stable)
- Redis
```

### 🔧 Instalação

Para iniciar la instalación del proyecto es necesario tener todas las herramientas de pré-requisitos disponibles para uso

#### Redis
```
- su - root
- docker run --name redis-${instancia_add} -p ${redis_port}:6379 --restart always --detach redis redis-server --requirepass ${root_password}
```

#### Postgres
```
- sudo su - postgres
- createdb ${instancia_add};
- psql
- CREATE USER ${instancia_add} SUPERUSER INHERIT CREATEDB CREATEROLE;
- ALTER USER ${instancia_add} PASSWORD '${root_password}';
```

#### .env backend
```
NODE_ENV=
BACKEND_URL=${backend_url}
FRONTEND_URL=${frontend_url}
PROXY_PORT=443
PORT=${backend_port}

DB_DIALECT=postgres
DB_HOST=localhost
DB_PORT=5432
DB_USER=${instancia_add}
DB_PASS=${mysql_root_password}
DB_NAME=${instancia_add}

JWT_SECRET=${jwt_secret}
JWT_REFRESH_SECRET=${jwt_refresh_secret}

REDIS_URI=redis://:${mysql_root_password}@127.0.0.1:${redis_port}
REDIS_OPT_LIMITER_MAX=1
REGIS_OPT_LIMITER_DURATION=3000

USER_LIMIT=${max_user}
CONNECTIONS_LIMIT=${max_whats}
CLOSED_SEND_BY_ME=true

GERENCIANET_SANDBOX=false
GERENCIANET_CLIENT_ID=Client_Id_Gerencianet
GERENCIANET_CLIENT_SECRET=Client_Secret_Gerencianet
GERENCIANET_PIX_CERT=certificado-Gerencianet
GERENCIANET_PIX_KEY=chave pix gerencianet

# EMAIL
 MAIL_HOST="smtp.gmail.com"
 MAIL_USER="seu@gmail.com"
 MAIL_PASS="SuaSenha"
 MAIL_FROM="seu@gmail.com"
 MAIL_PORT="465"

```

#### .env frontend
```
REACT_APP_BACKEND_URL=${backend_url}
REACT_APP_HOURS_CLOSE_TICKETS_AUTO = 24
```

#### Instalando dependencias
```
cd backend/
npm install --force
cd frontend/
npm install --force
```

### Rodando localmente
```
cd backend/
npm run watch
npm start

cd frontend/
npm start
```

## ⚙️ Executando los testes

//

### 🔩 Analise los testes de punta a punta

//

## 📦 Implantação em produção

Para correcta implantação é necessário realizar uma atualização do código fonte da aplicação e criar novamente os arquivos da pasta dist/

Atenção: é necessário acessar utilizando o usuário de deploy

```
su - deploy
```

```
cd /home/deploy/${empresa_atualizar}
pm2 stop ${empresa_atualizar}-frontend
git pull
cd /home/deploy/${empresa_atualizar}/frontend
npm install
rm -rf build
npm run build
pm2 start ${empresa_atualizar}-frontend
pm2 save
```

```
cd /home/deploy/${empresa_atualizar}
pm2 stop ${empresa_atualizar}-backend
git pull
cd /home/deploy/${empresa_atualizar}/backend
npm install
npm update -f
npm install @types/fs-extra
rm -rf dist 
npm run build
npx sequelize db:migrate
npx sequelize db:migrate
npx sequelize db:seed
pm2 start ${empresa_atualizar}-backend
pm2 save 
```

## 🛠️ Construído com


* [Express](https://expressjs.com/pt-br/) - O framework backend usado
* [React](https://react.dev/) - Framework frontend usado
* [NPM](https://www.npmjs.com/) - Gerenciador de dependencias

## 🖇️ Colaborando

//

## 📌 Versão

Versão 1.0.0

## 📄 Licença

Este proyecto está bajo la licencia

⌨️ con ❤️ por [Botia360](https://botia360.com.mx) 😊

Todos los derechos reservados a https://botia360.com.mx
