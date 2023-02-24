# Definição da imagem base com uma versão específica para garantir a idempotência da aplicação
FROM node:14.15.4

# Criação do diretório de trabalho
WORKDIR /app

# Cópia para o diretório corrente "/app" dos arquivos package.json e package-lock.json que possuem as definições dos pacotes necessários.
# Essa cópia está separada dos demais arquivos do projeto para melhor utilização e reaproveitamento do cache das camadas da imagem.
COPY package*.json ./

# Donwload e instalação dos pacotes do projeto
RUN npm install

# Cópia dos outros arquivos do projeto.
COPY . .

# Expor porta que a aplicação está utilizando para acesso externo
EXPOSE 8080

# Comando de inicialização do Container
CMD ["node", "app.js"]
