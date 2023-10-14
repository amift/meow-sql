# MeowSQL :scream_cat:

MeowSQL is an attempt to port a very useful GUI database client 
[HeidiSQL](https://www.heidisql.com/) to C++/Qt (with aim to be run natively at least on Linux)

![MeowSQL Gif](screenshots/meowsql.gif)

## Download/Install

Download installer for Windows or AppImage([how to run](https://appimage.org/)) 
for Linux on [releases](https://github.com/ragnar-lodbrok/meow-sql/releases) page.

## Features

The app is in development stage at the moment and was never carefully tested, 
though it can be run and do some work (warning: do not use in production!!!).

1. Works on Windows and Linux, in theory can be compiled on any platform with Qt5 and mysql-client support
2. At the moment supports MySQL and PostgreSQL (early stage).
3. Sessions manager: managing multiple connections (warn: no password encryption!) 
4. Connection to multiple sessions (=servers) at once (with multiple databases).
5. Tree of db objects like databases and tables/views/striggers/functions/procedures - (MySQL + Postgres).
6. Table: view columns (editable), indexes (editable) and foreign keys (editable) - (MySQL only).
7. Table: view data (basic edit) - (MySQL + Postgres).
8. SQL: editor with simple syntax highlighting (no autocomplete).
9. SQL: execute multiple statements at once and see results of SELECT statements 
10. Create and drop tables - (MySQL only)
11. Making dumps - (MySQL only via mysqldump)
12. Initial SQLite 3 support (read-only)

## Contributing

MeowSQL is a port of [HeidiSQL](https://github.com/HeidiSQL/HeidiSQL), 
so just clone the sources and start rewriting Delphi code to Qt/C++ :

1. Pick up any [issue](https://github.com/ragnar-lodbrok/meow-sql/issues) or any feature from [roadmap](ROADMAP.md).
2. Replace TODOs with working code :smile_cat:
3. Test the app and report bugs
4. Star the repo :star:


Use/subbranch develop, not master branch.

## How to build (for developers)

Note: both QMake and CMake are supported at the moment

Linux:

1. You need gcc (or other compiler) with c++11 support
2. Qt (tested with 5.6-5.15, apt-get install qt5-default) and QMake (Optionally: Qt Creator) or CMake
3. Clone the repo
4. libmysqlclient library, for deb-based distros: apt-get install libmysqlclient-dev
5. (Optional) Debian: sudo apt-get install mysql-server
6. (Optional) Install test db: https://dev.mysql.com/doc/sakila/en/
7. PostgreSQL client library libpq, for deb-based apt-get install libpq-dev postgresql-server-dev-all
8. As an option use Qt Creator - just open ./meow-sql.pro or ./CMakeLists.txt

Windows (Actual):

1. Download and install Qt 5 (5.6-5.15) via online-installer https://www1.qt.io/download-open-source/#section-2
2. You would need a cpp compiler of course, I've got MS Visual Studio 2017 (Community)
3. You should have CMake (already shipped with VS)
4. Install Conan from conan.io
5. Clone the repo and install conan packages (use your compiler/arch/etc):

        $ mkdir conan && cd conan
        $ conan install .. --settings arch=x86 --settings arch_build=x86 --settings build_type=Release --build=missing
6. Open ./CMakeLists.txt in VS or Qt Creator (QMake is not supported on Win!)
7. After build run windeployqt (or copy all libs from installed app)

Windows (Obsolete):

1. Download and install Qt via online-installer https://www1.qt.io/download-open-source/#section-2
Version that worked for me is Qt 5.6.2 win32-msvc2013
2. You would need a cpp compiler of course, I've got MS Visual Studio 2013 (Community)
3. You should have QMake (plus I used Qt Creator) or CMake
4. I've downloaded MySQL Connector C 6.1 (C not C++), and seems put all necessary files into third_party/
5. I've downloaded PostgreSQL's libpq, and seems put all necessary files into third_party/ 
(Note: seems CMAKE still looks into C:/Program Files, so try to download and install PG 10.7 32bits here https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)
6. As an option use Qt Creator - just open ./meow-sql.pro or ./CMakeLists.txt
7. After build (only release worked for me), run windeployqt (or copy all libs from installed app)

Mac OS:

1. Install XCode
2. Download and install Qt via online-installer https://www1.qt.io/download-open-source/#section-2 Install Version 5.9.8
3. You need to download MySQL Connector C and libpq. I recommend to use [homebrew](https://brew.sh/) and simply use `brew install mysql-connector-c libpq`
4. make sure header files are available in /usr/local/include. If you installed via homebrew just create symlink `ln -s /usr/local/opt/mysql-connector-c/include /usr/local/include/mysql/mysql` and `ln -s /usr/local/opt/libpq/include /usr/local/include/postgresql`
5. open ./meoq-sql.pro in Qt Creator and build
6. If you get errors about missing .dylib Files (e.g. libJPEG.dylib) make sure you uncheck "Add build library search path to DYLD_LIBRARY_PATH and DYLD_FRAMEWORK_PATH" in Project Settings in Qt Creator (see https://stackoverflow.com/questions/35509731/dyld-symbol-not-found-cg-jpeg-resync-to-restart)

## License

This project is licensed under the GPL 2.0 License

## Translations

If you want to translate MeowSQL to your language, open corresponding `resources/translations/meowsql_*.ts` file.

Use either Qt Linguist or in any text editor remove (` type="unfinished"`) from translation section:

`<translation type="unfinished">ADD TRANSLATION HERE</translation>`

Then create merge request (see also resources/translations/README.txt).

## Acknowledgments
* HeidiSQL developers - now on [github](https://github.com/HeidiSQL/HeidiSQL)
* [peek](https://github.com/phw/peek) was used for GIF recording
* [linuxdeployqt](https://github.com/probonopd/linuxdeployqt) was used for AppImage creation

## Donation
* One time (any amount + message): https://www.donationalerts.com/r/ragnar_lodbro
* Recurring: https://boosty.to/ragnar_lodbro
* Recurring: https://patreon.com/ragnar_lodbrok
* BTC: 1Ce8eJmJNDUxHdnqQGfgBVkLzixSBhEsaC
* USDT: TCyFuko2mxtduRc9SgPkZtPWUk7cPz3vZt
* TON: UQCinAVCbNfOxvOfsyBjtmKrZoQr6t1tQ5A-XLS3XwJanTwr

