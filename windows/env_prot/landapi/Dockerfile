FROM microsoft/iis
SHELL ["powershell"]

RUN Install-WindowsFeature NET-Framework-45-ASPNET; Install-WindowsFeature Web-Asp-Net45

COPY landing landing  
RUN Remove-WebSite -Name 'Default Web Site' 

RUN powershell -NoProfile -Command \
    Import-module IISAdministration; \
    New-IISSite -Name "landing" -PhysicalPath C:\landing -BindingInformation "*:80:"

RUN Windows\system32\inetsrv\appcmd.exe set AppPool /apppool.name:DefaultAppPool /processModel.identityType:LocalSystem

#EXPOSE 8000

CMD ["ping", "-t", "localhost"]