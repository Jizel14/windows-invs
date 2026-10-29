Get-AuthenticodeSignature "C:\Program Files\LogiDownloadAssistant\bin\logi_download_assistant.exe" | fl Status,StatusMessage,SignerCertificate
Get-ChildItem "C:\Program Files (x86)\GeoComply\PlayerLocationCheck\Application" -Recurse -Filter *.exe | Get-AuthenticodeSignature | ft Path,Status -AutoSize
