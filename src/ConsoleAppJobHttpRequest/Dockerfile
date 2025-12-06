# Alterar para mcr.microsoft.com/dotnet/sdk:9.0.308
FROM mcr.microsoft.com/dotnet/sdk:latest AS build-env
WORKDIR /app

# Copiar csproj e restaurar dependencias
COPY *.csproj ./
RUN dotnet restore

# Build da aplicacao
COPY . ./
RUN dotnet publish -c Release -o out

# Build da imagem
# Alterar para mcr.microsoft.com/dotnet/runtime:9.0.11
FROM mcr.microsoft.com/dotnet/runtime:9.0.8
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "ConsoleAppJobHttpRequest.dll"]
