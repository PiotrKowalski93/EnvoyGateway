FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build-env
WORKDIR /src

COPY *.csproj ./

RUN dotnet restore 

COPY . ./

RUN dotnet publish -c Release -o publish

FROM base as final
WORKDIR /app
COPY --from=build-env /src/publish .
ENTRYPOINT ["dotnet", "TeaAPI.dll"]