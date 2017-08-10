FROM microsoft/iis
SHELL ["powershell"]

RUN Install-WindowsFeature NET-Framework-45-ASPNET; Install-WindowsFeature Web-Asp-Net45

RUN mkdir webprojet
COPY landing webprojet/landing  
RUN Remove-WebSite -Name 'Default Web Site' 

RUN powershell -NoProfile -Command \
    Import-module IISAdministration; \
    New-IISSite -Name "webapi" -PhysicalPath C:\webprojet -BindingInformation "*:80:"

RUN Windows\system32\inetsrv\appcmd.exe add app /site.name:webapi /path:/api /physicalPath:C:\webprojet\landing 

RUN Windows\system32\inetsrv\appcmd.exe set AppPool /apppool.name:DefaultAppPool /processModel.identityType:LocalSystem

EXPOSE 80

CMD ["ping", "-t", "localhost"]