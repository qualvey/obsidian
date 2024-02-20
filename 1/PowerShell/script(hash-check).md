```
param (
    [string]$filePath,
    [string]$expectedHash
)

# 检查文件是否存在
if (-not (Test-Path $filePath -PathType Leaf)) {
    Write-Host "文件不存在：$filePath"
    exit
}

# 计算文件的哈希值
$actualHash = Get-FileHash -Path $filePath -Algorithm SHA256 | Select-Object -ExpandProperty Hash

# 比较哈希值
if ($actualHash -eq $expectedHash) {
    Write-Host "哈希值匹配：$actualHash"
} else {
    Write-Host "哈希值不匹配。实际哈希值：$actualHash"
}

```