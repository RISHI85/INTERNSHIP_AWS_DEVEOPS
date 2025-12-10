AWS-EC2
<img width="1476" height="1115" alt="Screenshot 2025-12-10 114720" src="https://github.com/user-attachments/assets/f57779cc-5c64-4aff-9692-f4b21d5f6d95" />

1. Launch instance with windows as AMI

2. Create a key pair with .pem

3. paste the user data in the advanced details 

user data for automatic chrome in RDP:

<powershell>

# Download Google Chrome
$ChromeInstaller = "https://dl.google.com/chrome/install/latest/chrome_installer.exe"
$ChromePath = "C:\Windows\Temp\chrome_installer.exe"

Invoke-WebRequest -Uri $ChromeInstaller -OutFile $ChromePath

# Install Chrome silently
Start-Process -FilePath $ChromePath -ArgumentList "/silent /install" -Wait

# Set Chrome as default browser
$chromeProgId = "ChromeHTML"
$regPath = "HKCU:\Software\Microsoft\Windows\Shell\Associations\UrlAssociations\http\UserChoice"
New-Item -Path $regPath -Force | Out-Null
Set-ItemProperty -Path $regPath -Name "ProgId" -Value $chromeProgId

# Apply same for https links
$regPath2 = "HKCU:\Software\Microsoft\Windows\Shell\Associations\UrlAssociations\https\UserChoice"
New-Item -Path $regPath2 -Force | Out-Null
Set-ItemProperty -Path $regPath2 -Name "ProgId" -Value $chromeProgId

Write-Host "Google Chrome installed & set as default browser successfully"

</powershell>


4.  click launch instance

5. click connect

6. RDP Client

7. download RDP FILE

8. get password

9. place pem folder and get the password

10. copy the password 

11. open the downloaded rdp file and place the password 

12. you can see the windows administrator with chrome automatically downloaded
