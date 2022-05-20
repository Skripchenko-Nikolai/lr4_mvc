FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["lr4/lab4.csproj", "lab4/"]
RUN dotnet restore "lab2_MVC/lab2_MVC.csproj"
COPY . .
WORKDIR "/src/lar4"
RUN dotnet build "lab4.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "lab4.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "lab4.dll"]
