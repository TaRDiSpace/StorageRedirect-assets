### Behavior changes of redirected app

* Reading and writing files and folders other than _standard folders_ will be redirected to `/Android/data/<package>/cache/sdcard`

  For example, suppose you have an app named aaa (package: `example.aaa`) that actually writes (or reads) `/sdcard/Android/data/example.aaa/cache/sdcard` when it writes (or reads) `/sdcard/aaa/blbl.txt`, but not the files in _standard folders_.

* Files written outside the _standard folders_ are managed by Android system
  * These files are accounted in storage usage
  * These files will be removed when clear app cache (or data) from system _App info_

> Standard folders refer to folders that Android will create by default, such as `Android`, `Pictures`, `Music` and so on. In future versions it is possible to specify separately for each application what is a standard folder.

### Situations that affect the normal usage of redirected app

* The app uses system's _Download Manager_. If the downloaded file is saved outside of _standard folder_, the app is not accessible to the file
* The app will not able to access files and folders outside of _standard folder_. App's feature such as send picture or send file will be affected of the file is not in _standard folder_

### Note

* Redirected app will be force stopped when turning on redirecting
* Because files in `/sdcard` do not have a specific owner, files created by redirected app previously need to be deleted manually