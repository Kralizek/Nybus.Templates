FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
WORKDIR /app
COPY * ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/runtime:2.2 AS runtime
WORKDIR /app
COPY --from=build  /app/out ./
ENV NYBUS_ENVIRONMENT=Production
ENTRYPOINT [ "dotnet", "NetCoreRabbitMq.dll" ]