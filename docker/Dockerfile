
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /usr/src
# copy csproj and restore as distinct layers
COPY *.csproj .
RUN dotnet restore

# copy and publish app and libraries
COPY . .
RUN dotnet publish -c release -o /app
# final stage/image
FROM mcr.microsoft.com/dotnet/runtime:6.0

WORKDIR /app
COPY --from=build /app .



ENTRYPOINT ["dotnet", "worker.dll"]