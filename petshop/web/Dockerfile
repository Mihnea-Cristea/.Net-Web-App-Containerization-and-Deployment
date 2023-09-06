FROM mcr.microsoft.com/dotnet/framework/aspnet:3.5-windowsservercore-ltsc2019
SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';"]

RUN Install-WindowsFeature NET-HTTP-Activation; \
    Remove-Website -Name 'Default Web Site'; \
    New-Website -Name 'petshop-web' -Port 80 -PhysicalPath 'C:\petshop-web' -Force

COPY petshop-web.zip .
RUN Expand-Archive -Path petshop-web.zip -DestinationPath /
COPY web.config /petshop-web/