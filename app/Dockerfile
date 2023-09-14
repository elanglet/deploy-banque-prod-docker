FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS runtime
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

WORKDIR /src
COPY ./deploy .
RUN dotnet restore
RUN dotnet build -o /app/build
RUN dotnet publish -o /app/publish

FROM runtime AS final
WORKDIR /app
COPY --from=build /app/publish .
EXPOSE 80

ENTRYPOINT ["dotnet", "banque-portail-net.dll"]
