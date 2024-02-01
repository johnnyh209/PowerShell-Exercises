# 5.6 Lab

1. Create a new directory called Labs.
- New-Item -path C:\Users\Admin\Desktop -itemtype directory -name Labs

2. Create a zero-length file named /Labs/Test.txt.
- new-item -path C:\Users\Admin\Desktop\Labs -itemtype file -name Test.txt

3. Is it possible to use `Set-Item` to change the contents of /Labs/Test.txt to `-TESTING`? Or do you get an error? If you get an error, why?
- It is not possible. `Set-Item` cannot be used to change/modify the contents of a file.

4. Using the Environment provider, display the value of the system environment variable `PATH`.
- Set-Location Env: -> Get-ChildItem
or 
- Get-Item Env:Path

5. Use help to determine what the differences are between the `-Filter`, `-Include`, and `-Exclude` parameters of Get-ChildItem.
- For `-Filter`, the only installed provider that supports this parameter is the `FileSystem` provider. `-Recurse` needs to be used with `-Include` and `-Exclude`.
