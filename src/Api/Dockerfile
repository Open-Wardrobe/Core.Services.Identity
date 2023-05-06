# BUILD STAGE
#---------------------------------------------------------------------
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env
WORKDIR /app

# Copy everything
COPY . .

# Restore as distinct layers
RUN dotnet restore
# Build and publish a release

# WORKDIR /src/Api

RUN dotnet publish src/Api -c Release -o build-out

# RUNTIME STAGE
#---------------------------------------------------------------------

FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app
COPY --from=build-env /app/build-out .
ENTRYPOINT ["dotnet", "OpenWardrobe.Core.Services.Identity.Api.dll"]










# FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
# WORKDIR /app












# FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
# WORKDIR /app

# # Copy everything
# COPY "Identity.sln" "Identity.sln"
# COPY "src/Api/Api.csproj" "src/Api/Api.csproj"
# COPY "tests/Api.FunctionalTests/Api.FunctionalTests.csproj" "tests/Api.FunctionalTests/Api.FunctionalTests.csproj"
# COPY "tests/Api.FunctionalTests/Api.FunctionalTests.csproj" "tests/Api.FunctionalTests/Api.FunctionalTests.csproj"
# COPY "NuGet.config" "NuGet.config"

# # # Restore as distinct layers
# # RUN dotnet restore
# RUN dotnet restore "Identity.sln"

# COPY . .

# # # 
# # WORKDIR /src/Identity/Api
# # RUN dotnet publish --no-restore -c Release -o /app

# # FROM build AS publish

# # FROM base AS final
# # WORKDIR /app
# # COPY --from=publish /app .
# # ENTRYPOINT ["dotnet", "Identity.API.dll"]


# # # Build and publish a release
# # RUN dotnet publish -c Release -o out

# # # Build runtime image
# # FROM mcr.microsoft.com/dotnet/aspnet:7.0
# # WORKDIR /app
# # COPY --from=build-env /App/out .
# # ENTRYPOINT ["dotnet", "DotNet.Docker.dll"]