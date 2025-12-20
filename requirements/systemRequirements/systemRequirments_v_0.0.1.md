# System Requirements For Version 0.0.1

**Id** : **Req-0.0.1-01**

**Name** : **Explore Linux File System Using Command-line Interface**

**Function** : System shall take a command from a user, once at a time, system shall process those commands and output what user needs.

**Inputs** : 
```bash
file-explore --[commands] [Params]
```
**Output** : Each output should be explored on each specific requirements

**Description** : 
1. System shall take user input as commands from any Linux terminal. 
2. System shall process those input command then validate if input are valid.
3. If input command and parameters are valid and correct System shall output JSON formated object. 
4. If input command or parameters are invalid, System shall output Error JSON object with description for error and a error command.

**Pre Condition** : System shall check for currentPath in `/tmp/file-explore/currentPath.conf`

**Post Condition** : If user change path while using system, last path that user was in should be written into `/tmp/file-explore/currentPath.conf` file.

**Author** : W.A. Rajinda


---

**Id** : **Req-0.0.1-02**

**Name** : **Creating updating current path user in on `/tmp/file-explore/`**

**Function** : System shall record file path of user is currently in or user will change into

**Description** : 
1. System shall get the current path user is in
2. System shall write current path in to `currentPath.conf` in `/tmp/file-explore/` as path=/path/name
3. System shall read from `/tmp/file-explore/currentPath.conf` when system required to.
4. System shall forget all records after application shutdown and begin from user's home directory when system reopen.

**Pre Condition** :
1. System shall look if `/tmp/file-explore` folder exist.
2. If folder doesn't exist, system should create `/tmp/file-explore` folder
3. System should read current path from `/tmp/file-explore/currentPath.conf`
4. If currentPath.conf file is empty or not found, System shall create `/tmp/file-explore/currentPath.conf` file then set current path as current USER's `home` folder, then load currentPath.conf.

---

**Id** : **Req-0.0.1-03**

**Name** : **List all files and folders in a given path**

**Function** : System shall list all files and folders with their meta-data in a JSON formate

**Inputs** : System shall take user input as a bash command in a Linux terminal.
```bash
file-explore --all </path/to/folder or leave it empty>
```

**Output** : System shall output formated JSON object

**Description**
1. System shall take input command as describe in `Inputs` section.
2. System shall take folder path in the Linux filesystem as a parameter to `--all`.
3. Parameters, provided with command should be a valid path to a folder or user should leave parameters empty.
4. If provided path is invalid, system shall return an error object as,

    ```json
    {
      "errorCode": "Err-0.0.1-03",
      "description": "Provided path to the folder is an invalid path."
    }
    ```
5. If user didn't provide a path to folder, folder path should be loaded form `/tmp/file-explore/currentPath.conf`
6. When system validate parameters, system should take that folder path then get all files and folder.
7. When system get files, system shall get file's name, file size in appropriate units, last modified date, file path from root directory.
8. When system get folders, system shall get folder's name, cumulative size (including contents), created date of the folder.
9. System shall output all files and folders in a JSON object as,

    ```json
    {
      "files": [
        {
          "name": "file name",
          "size": "file size",
          "lastModifiedDate": "last modified data as year/month/date-HH:MM:SS",
          "filePath": "/path/to/file"
        }
      ],
      "folder": [
        {
          "name": "folder name",
          "size": "folder size",
          "createdDate": "create date in year/month/data-HH:MM:SS"
        }
      ]
    }
    ```
10. System shall not physically move to user given folder.
11. System only need to retrieve file and folder information

**Pre Condition** : check for `/tmp/file-explore/currentPath.conf` as stated in **`Req-0.0.1-02`**.

**Post Condition** : update `/tmp/file-explore/currentPath.conf` file as stated in **`Req-0.0.1-02`**.

**Author** : W.A. Rajinda

**Risk** : Low

**Last Updated** : 2025/12/20

---
