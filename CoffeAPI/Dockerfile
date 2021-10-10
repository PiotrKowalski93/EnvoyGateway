FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
ENTRYPOINT dotnet dev-certs https --trust

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build-env
WORKDIR /src

COPY *.csproj ./

RUN dotnet restore 

COPY . ./

RUN dotnet publish -c Release -o publish

FROM base as final
WORKDIR /app
COPY --from=build-env /src/publish .
ENTRYPOINT ["dotnet", "CoffeAPI.dll"]