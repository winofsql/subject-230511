### インストール
![image](https://github.com/winofsql/subject-230511/assets/1501327/b392d1c1-bed4-49e1-835f-4b69e0d796ad)

![image](https://github.com/winofsql/subject-230511/assets/1501327/c088909d-3138-4b9e-8ec7-470de0e0a51c)

![image](https://github.com/winofsql/subject-230511/assets/1501327/2156ad2c-b9df-4bd1-a409-d224927421e4)

![image](https://github.com/winofsql/subject-230511/assets/1501327/e542698b-c1b4-4e04-b41f-7fd08d5e8ae8)

![image](https://github.com/winofsql/subject-230511/assets/1501327/68664123-b033-4da1-af8e-ca538844044e)

![image](https://github.com/winofsql/subject-230511/assets/1501327/27e27329-76ee-4317-b934-16436606a51f)

![image](https://github.com/winofsql/subject-230511/assets/1501327/69c01250-dc02-4a78-bf32-d32bebc1d685)

![image](https://github.com/winofsql/subject-230511/assets/1501327/a7e4d94b-9518-4fe0-832c-1ce707a0d6e2)

![image](https://github.com/winofsql/subject-230511/assets/1501327/33457034-068a-4578-9e4e-46cee8718561)

### ここまでを G ドライブを使って実行するスクリプト
```vbscript
Set objShellApplication = CreateObject("Shell.Application")
If WScript.Arguments.Count = 0 Then
    objShellApplication.ShellExecute "cscript.exe", Chr(34) & WScript.ScriptFullName & Chr(34) & " dummy", "", "runas", 1
	Wscript.Quit
End If

Set objShell = CreateObject("WScript.Shell")
Set objFSO = CreateObject("Scripting.FileSystemObject")

target0 = "c:\pleiades"
target1 = "c:\app"
target2 = "c:\app\java23"
target3 = "c:\app\java23\subject-0511"

If not objFSO.FolderExists(target1) Then

	objFSO.CreateFolder(target1)

End If
If not objFSO.FolderExists(target2) Then

	objFSO.CreateFolder(target2)

End If
If not objFSO.FolderExists(target3) Then

	objFSO.CreateFolder(target3)

End If

If not objFSO.DriveExists("G:") Then
	MsgBox("G ドライブがありません。Google ドライブを実行してください")
	Wscript.Quit
End If

If not objFSO.FolderExists("G:\共有ドライブ\SE-WORK-DOWNLOAD") Then
	MsgBox("SE-WORK-DOWNLOAD フォルダが共有フォルダにありません。対象となるアカウントでログインして下さい")
	Wscript.Quit
End If

SevenZipPath = objShell.RegRead("HKLM\SOFTWARE\7-Zip\Path") & "7z.exe"

If not objFSO.FolderExists(target0) Then

	Wscript.Echo "pleiades.zip を copy しています。しばらくお待ちください"

	Set sourceFile = objFSO.GetFile("G:\共有ドライブ\SE-WORK-DOWNLOAD\java\pleiades.zip")
	sourceFile.Copy target0 & ".zip", True

	Wscript.Echo "pleiades.zip の copy が終了しました"

	Wscript.Echo "pleiades.zip を 解凍しています。しばらくお待ちください"

	objShell.Run Chr(34) & SevenZipPath & Chr(34) & " x -o" & target0 & " " & target0 & ".zip", 0, True

	Wscript.Echo "pleiades.zip の 解凍が終了しました"

End If

MsgBox("pleiades 設定を終了しました。")
```

### いったん Eclipse を閉じる
- ショートカット作成
- 実行
- パースペクティブを Java に変更
- Java プロジェクト作成
- src を選択して Class 作成
  - Main
  - public static void main にチェック
- 自動 import は CTRL + SHIFT + O


