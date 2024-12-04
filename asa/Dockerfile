FROM mcr.microsoft.com/dotnet/sdk:8.0 AS builder 
WORKDIR /app
EXPOSE 80
EXPOSE 443
COPY . .
RUN dotnet restore
RUN dotnet publish -c Release -o output
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=builder /app/output .
ENTRYPOINT ["dotnet", "asa.dll"]