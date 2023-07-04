FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["FoolGameWebApp.csproj", ""]
RUN dotnet restore "./FoolGameWebApp.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "FoolGameWebApp.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "FoolGameWebApp.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "FoolGameWebApp.dll"]
