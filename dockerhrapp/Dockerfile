#first stage base image
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build 
WORKDIR /source  

#copy cs project and restore dependencies
COPY *.csproj  .
RUN dotnet restore 

#copy and publish the application files
COPY . . 
RUN dotnet publish -c release -o /app

#final stage image 
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet","hrapp.dll"]


