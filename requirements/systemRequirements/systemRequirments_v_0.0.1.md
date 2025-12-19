# System Requirements For Version 0.0.1

**Id** : Req-0.0.1-01

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

**Pre Condition** : 
1. System shall look if `/tmp/file-explore` folder exist. 
2. If folder doesn't exist, system should create `/tmp/file-explore` folder
3. System should read current path from `/tmp/file-explore/currentPath.conf`
4. If currentPath.conf file is empty or not found, System shall create `/tmp/file-explore/currentPath.conf` file then set current path as current USER's `home` folder, then load currentPath.conf.

**Post Condition** : If user change path while using system, last path that user was in should be written into `/tmp/file-explore/currentPath.conf` file.

**Author** : W.A. Rajinda


---

