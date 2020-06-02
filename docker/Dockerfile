
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base

# Build app
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src/watchguide-api
COPY src .
#RUN dotnet restore -nowarn:msb3202,nu1503
RUN dotnet build -c Release -o /app

# Publish app
FROM build AS publish
RUN dotnet publish -c Release -o /app

# Create final Image
FROM base AS final
WORKDIR /app
COPY --from=publish /app .

# Start app
ENTRYPOINT ["dotnet", "dotnetCoreAPI.dll"]
