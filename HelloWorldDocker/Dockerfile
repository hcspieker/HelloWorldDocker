FROM		mcr.microsoft.com/dotnet/sdk:10.0-alpine AS build
WORKDIR		/app

COPY		*.csproj ./
RUN			dotnet restore

COPY		. ./
RUN			dotnet publish "./HelloWorldDocker.csproj" -c Release -o /app/publish /p:UseAppHost=false


FROM		mcr.microsoft.com/dotnet/aspnet:10.0.2-alpine3.23-composite AS runtime
WORKDIR		/app
COPY		--from=build /app/publish ./

ENV			ASPNETCORE_URLS="http://*:80"
EXPOSE		80

ENTRYPOINT	["dotnet", "HelloWorldDocker.dll"]
