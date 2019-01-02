FROM microsoft/dotnet:2.2.100-sdk-alpine3.8 AS build
WORKDIR /app
COPY *.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c Debug -o out

FROM microsoft/dotnet:2.2.0-aspnetcore-runtime-alpine3.8
EXPOSE 80
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "Example.App.dll"]
