FROM mcr.microsoft.com/dotnet/sdk:6.0 AS base
WORKDIR /App

# Copy everything
COPY . ./
# Restore as distinct layers
RUN dotnet restore
# Build and publish a release
RUN dotnet publish -c Release -o out

# Build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:6.0

WORKDIR /App


COPY --from=base /App/out .
ENTRYPOINT ["dotnet", "PokemonReviewApp.dll"]
