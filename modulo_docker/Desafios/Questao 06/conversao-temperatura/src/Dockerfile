# Definição da imagem base
FROM node

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
CMD ["node", "server.js"]
