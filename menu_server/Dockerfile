# Use the official .NET SDK image for building the app
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Copy the project files and restore dependencies
COPY *.csproj ./
RUN dotnet restore

# Copy the remaining source code and publish the app
COPY . ./
RUN dotnet publish -c Release -o out

# After publishing, check output directory
RUN ls -la out

# Use the official ASP.NET runtime image to run the app
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/out ./

# Expose the port the app runs on
EXPOSE 5000

# Run the app
ENTRYPOINT ["dotnet", "menu_server.dll"]
