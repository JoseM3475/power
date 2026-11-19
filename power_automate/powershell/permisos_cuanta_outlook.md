# Conceder permiso "Send As"
```PowerShell
Connect-ExchangeOnline
```

## Crear una Shared Mailbox

### Instalar módulos
```Powershell
Install-Module ExchangeOnlineManagement
Import-Module ExchangeOnlineManagement
```

### Conectarse a Exchange Online
```Powershell
Connect-ExchangeOnline
```
### Crear el buzón compartido
```Powershell
New-Mailbox `
    -Shared `
    -Name "Automatizaciones" `
    -DisplayName "Automatizaciones" `
    -PrimarySmtpAddress automatizaciones@zg7wc.onmicrosoft.com
```
### Conceder permisos de acceso

Add-MailboxPermission `
    -Identity automatizaciones@zg7wc.onmicrosoft.com `
    -User AlexW@zg7wc.onmicrosoft.com `
    -AccessRights FullAccess `
    -InheritanceType All

### Conceder permiso Send As

Add-RecipientPermission `
    -Identity automatizaciones@zg7wc.onmicrosoft.com `
    -Trustee alex@empresa.com `
    -AccessRights SendAs

### Verificar la configuración

### Comprobar el buzón:

PowerShell
Get-Mailbox powerautomate@empresa.com

### Comprobar permisos Full Access:

PowerShell
Get-MailboxPermission powerautomate@empresa.com

Comprobar permisos Send As:

PowerShell
Get-RecipientPermission powerautomate@empresa.com
