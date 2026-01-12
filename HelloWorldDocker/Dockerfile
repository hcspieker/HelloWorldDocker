FROM		mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR		/app

# Copy csproj first for faster rebuilds, then restore and publish
COPY		*.csproj ./
RUN			dotnet restore

COPY		. ./
RUN			dotnet publish "./HelloWorldDocker.csproj" -c Release -o /app/publish /p:UseAppHost=false


FROM		mcr.microsoft.com/dotnet/aspnet:10.0 AS runtime
WORKDIR		/app
COPY		--from=build /app/publish ./

ENV			ASPNETCORE_URLS="http://*:50005"
EXPOSE		50005

ENTRYPOINT	["dotnet", "HelloWorldDocker.dll"]

# test command: docker build -t helloworlddockertest . ; docker run --rm -p 8081:50005 helloworlddockertest
