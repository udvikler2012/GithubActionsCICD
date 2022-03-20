#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

#Restore Stage
WORKDIR /src
COPY ["WebAppDemoNet6/WebAppDemoNet6.csproj", "WebAppDemoNet6/"]
RUN dotnet restore "WebAppDemoNet6/WebAppDemoNet6.csproj"

#Build Stage
COPY . .
WORKDIR "/src/WebAppDemoNet6"
RUN dotnet build "WebAppDemoNet6.csproj" -c Release -o /app/build

#Publish Stage
FROM build AS publish
RUN dotnet publish "WebAppDemoNet6.csproj" -c Release -o /app/publish

#Deploy Stage
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebAppDemoNet6.dll"]