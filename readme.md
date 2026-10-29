Get-AuthenticodeSignature "C:\Program Files\LogiDownloadAssistant\bin\logi_download_assistant.exe" | fl Status,StatusMessage,SignerCertificate
Get-ChildItem "C:\Program Files (x86)\GeoComply\PlayerLocationCheck\Application" -Recurse -Filter *.exe | Get-AuthenticodeSignature | ft Path,Status -AutoSize
$f = "C:\Program Files\LogiDownloadAssistant\bin\logi_download_assistant.exe"
Get-FileHash $f -Algorithm SHA256
Get-Item $f | Select CreationTime, LastWriteTime, Length
(Get-Item $f).VersionInfo | fl CompanyName, ProductName, FileVersion
Get-ItemProperty HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\*, HKLM:\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\* | ? DisplayName -like "*Logi*" | Select DisplayName, InstallDate

$f = "C:\Program Files\LogiDownloadAssistant\bin\logi_download_assistant.exe"
(Get-Item $f).VersionInfo | fl CompanyName, ProductName, FileVersion
Get-Item $f | Select CreationTime, LastWriteTime
Get-Process logi_download_assistant -ErrorAction SilentlyContinue | Select Id, StartTime
Get-CimInstance Win32_Product -Filter "Name like '%Logi%'" | Select Name, Version, InstallDate
