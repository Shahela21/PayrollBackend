FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /bepayroll_appconfig
COPY . .
RUN dotnet restore -s http://proget/nuget/SDWorxNuget
RUN dotnet publish --no-restore -c Release -o ../dist

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS runtime
WORKDIR /bepayroll_appconfig
COPY --from=build /bepayroll_appconfig/dist ./

ENV ASPNETCORE_URLS http://+:5005
EXPOSE 5005

ENTRYPOINT ["dotnet", "SDWorx.BePayroll.AppConfig.Api.dll"]