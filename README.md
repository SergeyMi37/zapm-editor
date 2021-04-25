![](https://raw.githubusercontent.com/SergeyMi37/zapm-editor/master/doc/zed-blue.png)

## zapm-editor
[![Gitter](https://img.shields.io/badge/Available%20on-Intersystems%20Open%20Exchange-00b2a9.svg)](https://openexchange.intersystems.com/package/zapm-editor)
[![GitHub all releases](https://img.shields.io/badge/Available%20on-GitHub-black)](https://github.com/SergeyMi37/zapm-editor)
[![Habr](https://img.shields.io/badge/Available%20article%20on-Intersystems%20Community-orange)](https://community.intersystems.com/post/full-screen-editor-routines-arrays-and-text-files-terminal-mode)

[![](https://img.shields.io/badge/InterSystems-IRIS-blue.svg)](https://www.intersystems.com/products/intersystems-iris/)
[![](https://img.shields.io/badge/InterSystems-Caché-blue.svg)](https://www.intersystems.com/products/cache/)
[![](https://img.shields.io/badge/InterSystems-Ensemble-blue.svg)](https://www.intersystems.com/products/ensemble/)

[![license](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


File system explorer, ZPM module navigator, program editor, array editor and text file editor in terminal mode.

## Installation with ZPM

If ZPM the current instance is not installed, then in one line you can install the latest version of ZPM.
```
set $namespace="%SYS", name="DefaultSSL" do:'##class(Security.SSLConfigs).Exists(name) ##class(Security.SSLConfigs).Create(name) set url="https://pm.community.intersystems.com/packages/zpm/latest/installer" Do ##class(%Net.URLParser).Parse(url,.comp) set ht = ##class(%Net.HttpRequest).%New(), ht.Server = comp("host"), ht.Port = 443, ht.Https=1, ht.SSLConfiguration=name, st=ht.Get(comp("path")) quit:'st $System.Status.GetErrorText(st) set xml=##class(%File).TempFilename("xml"), tFile = ##class(%Stream.FileBinary).%New(), tFile.Filename = xml do tFile.CopyFromAndSave(ht.HttpResponse.Data) do ht.%Close(), $system.OBJ.Load(xml,"ck") do ##class(%File).Delete(xml)
```
If ZPM is installed, then ZAPM can be set with the command
```
zpm:USER>install zapm-editor
```
## Installation with Docker

### Prerequisites
Make sure you have [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and [Docker desktop](https://www.docker.com/products/docker-desktop) installed.

## Installation 
Clone/git pull the repo into any local directory

```
$ git clone https://github.com/SergeyMi37/zapm-editor.git
```

Open the terminal in this directory and run:

```
$ docker-compose build
```

Run the IRIS container with your project:

```
$ docker-compose up -d
```

## How to Test it
Open IRIS terminal:
```
$ docker-compose exec iris iris session iris

USER>
USER>zapm "edit-file cpf"
```
```
USER>zapm "edit-file D:\InterSystems\IRIS\iris.cpf"
```
![](https://raw.githubusercontent.com/SergeyMi37/zapm-editor/master/doc/Screenshot_8.png)

## Namespace navigator ZPM 

```
USER>zapm "edit-file zpm"
```
![](https://raw.githubusercontent.com/SergeyMi37/zapm-editor/master/doc/Screenshot_1.png)
![](https://raw.githubusercontent.com/SergeyMi37/zapm-editor/master/doc/Screenshot_2.png)
![](https://raw.githubusercontent.com/SergeyMi37/zapm-editor/master/doc/Screenshot_3.png)

## Routines editor 
```
USER>zapm "edit-rou"
```
![](https://raw.githubusercontent.com/SergeyMi37/zapm-editor/master/doc/Screenshot_4.png)
![](https://raw.githubusercontent.com/SergeyMi37/zapm-editor/master/doc/Screenshot_5.png)

## Globals editor 
```
USER>zapm "edit-glo"
```
![](https://raw.githubusercontent.com/SergeyMi37/zapm-editor/master/doc/Screenshot_6.png)

```
USER>zapm "edit-file mess"
```
![](https://raw.githubusercontent.com/SergeyMi37/zapm-editor/master/doc/Screenshot_7.png)
