FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS runtime
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

WORKDIR /src
COPY ./deploy .
ENV ASPNETCORE_ENVIRONMENT=Production
RUN dotnet restore
RUN dotnet build -o /app/build
RUN dotnet publish -o /app/publish

FROM runtime AS final
WORKDIR /app
ENV ASPNETCORE_ENVIRONMENT=Production
COPY --from=build /app/publish .
EXPOSE 80

ENTRYPOINT ["dotnet", "banque-portail-net.dll", "--no-launch-profile"]
