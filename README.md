# navicat-refresh

### Version
- Navicat Premium 15 & 16 (Windows)

### Delete Navicat Registry File
- HKEY_CURRENT_USER\Software\PremiumSoft\NavicatPremium\Registration[version and language]
    - ex : Registration15XCT, Registration16XEN
- HKEY_CURRENT_USER\Software\Classes\CLSID\\ * \Info
    - Delete all "Info" folder under CLSID (Parent folder name of Info may vary from person to person)
    - Be sure that will not delete other important file



### ARQUIVO .BAT para deletar de forma mais rapida

@echo off

:: Excluir a chave no caminho HKEY_CURRENT_USER\Software\PremiumSoft\Navicat\Registration16XEN
reg delete "HKEY_CURRENT_USER\Software\PremiumSoft\Navicat\Registration16XEN" /f

:: Encontrar e excluir a chave no caminho HKEY_CURRENT_USER\Software\Classes\CLSID\*\Info
for /f "tokens=*" %%a in ('reg query HKEY_CURRENT_USER\Software\Classes\CLSID /s /f "Info" ^| find "HKEY_CURRENT_USER\Software\Classes\CLSID"') do (
    reg delete "%%a" /f
)

echo Chaves do Registro excluídas com sucesso.
pause
