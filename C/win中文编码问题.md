mingw的gcc编译含中文字符串的程序，输出是乱码
问题确实出在windows上
解决方案:
```powershell
$OutputEncoding = [console]::InputEncoding = [console]::OutputEncoding = New-Object System.Text.UTF8Encoding
```
```
(base) PS C:\Users\intmain\Music> [System.Console]::OutputEncoding
                                                                                                                        Preamble          :
BodyName          : utf-8
EncodingName      : Unicode (UTF-8)
HeaderName        : utf-8
WebName           : utf-8
WindowsCodePage   : 1200
IsBrowserDisplay  : True
IsBrowserSave     : True
IsMailNewsDisplay : True
IsMailNewsSave    : True
IsSingleByte      : False
EncoderFallback   : System.Text.EncoderReplacementFallback
DecoderFallback   : System.Text.DecoderReplacementFallback
IsReadOnly        : False
CodePage          : 65001
```