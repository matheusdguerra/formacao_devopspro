# See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

# Imagem para build
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
# Cópia apenas arquivo com requisitos e baixa os pacotes
COPY ["src/PedeLogo.Catalogo.Api/PedeLogo.Catalogo.Api.csproj", "src/PedeLogo.Catalogo.Api/"]
RUN dotnet restore "src/PedeLogo.Catalogo.Api/PedeLogo.Catalogo.Api.csproj"
# Cópia do restante dos arquivos da aplicação
COPY . .
WORKDIR "/src/src/PedeLogo.Catalogo.Api"
# compila a aplicação colocando a release na pasta /app/build
RUN dotnet build "PedeLogo.Catalogo.Api.csproj" -c Release -o /app/build

# Criação dos arquivos de publicação a partir da imagem "build" colocando a release na pasta /app/publish
FROM build AS publish
RUN dotnet publish "PedeLogo.Catalogo.Api.csproj" -c Release -o /app/publish

# Criação de imagem de execução
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "PedeLogo.Catalogo.Api.dll"]