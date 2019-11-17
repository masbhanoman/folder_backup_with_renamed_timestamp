# folder_backup_with_renamed_timestamp
This script takes a snapshot(copies files and folder) of a directory even the file is in use or a folder is empty. Useful when you need backup of a drive every-after sometime. Task scheduler is a must to run the script every after sometime.  

@echo off
for /f "tokens=2 delims==" %%a in ('wmic OS Get localdatetime /value') do set "dt=%%a"
set "YY=%dt:~2,2%" & set "YYYY=%dt:~0,4%" & set "MM=%dt:~4,2%" & set "DD=%dt:~6,2%"
set "HH=%dt:~8,2%" & set "Min=%dt:~10,2%" & set "Sec=%dt:~12,2%"

set "datestamp=%YYYY%%MM%%DD%" & set "timestamp=%HH%%Min%%Sec%"
set "fullstamp=%DD%-%MM%-%YYYY%_%HH%_%Min%_%Sec%"

md "D:\project_backup\#test_projects_backup_%fullstamp%"

xcopy "\\192.168.2.30\taps\#test_projects" "D:\project_backup\#test_projects_backup_%fullstamp%" /e  /y

save line 4 to 14 with .bat extension and it will create a backup.
