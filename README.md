# PRÁCTICA GUIADA GIT/GITHUB

[1. Inicialización (init y status)](#1-inicialización-init-y-status)  
[2. Añadiendo archivos (add y commit)](#2-añadiendo-archivos-add-y-commit)  
[3. Modificando archivos](#3-modificando-archivos)  
[4. Información (git show y git log)](#4-información-git-show-y-git-log)  
[5. Diferencias (git diff)](#5-diferencias-git-diff)  
[6. Ignorar archivos (.gitignore)](#6-ignorar-archivos-gitignore)  
[7. Tags y gestión de versiones (git tag y git checkout)](#7-tags-y-gestión-de-versiones-git-tag-y-git-checkout)  
[8. Ramas](#8-ramas)  
[9. Eliminar y quitar de seguimiento](#9-eliminar-y-quitar-de-seguimiento)  
[10. Repositorios remotos: GitHub](#10-repositorios-remotos-github)  

## Introducción
```bash
mkdir prueba_git
cd prueba_git
nano texto.txt 
nano script.sh
chmod a+x script.sh
./script.sh
```
 
```text
-rw-r--r-- 1 AdrianSS 197121 28 Oct  8 09:42 script.sh
-rw-r--r-- 1 AdrianSS 197121 13 Oct  8 09:27 texto.txt
```

## 1. Inicialización (init y status)
```bash
git init
```

```text
Initialized empty Git repository in C:/Users/AdrianSS/prueba_git/.git/
```

```bash
git status
```

```text
On branch master
No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        script.sh
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)
```

```bash
AdrianSS@DESKTOP-KB9PHSP MINGW64 ~/prueba_git (master)   
$ git branch -m main

AdrianSS@DESKTOP-KB9PHSP MINGW64 ~/prueba_git (main)
$ git branch -m master
```

## 2. Añadiendo archivos (add y commit)

```bash
git add script.sh  
```
```text
warning: in the working copy of 'script.sh', LF will be replaced by CRLF the next time Git touches it
```

```bash
git status
```

```text
On branch master
No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:     script.sh

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt
```

```bash
git commit -m "Confirmación inicial"
```

```text
[master (root-commit) 6b588d9] Confirmación inicial
 1 file changed, 2 insertions(+)
 create mode 100644 script.sh
```

```bash
git status
```
```text
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)
```

```bash
git add texto.txt
```

```bash
git commit -m "Añadido archivo texto.txt"
```
```text
[master 32462a8] Añadido archivo texto.txt
 1 file changed, 3 insertions(+)
 create mode 100644 texto.txt
```

```bash
git status
```
```text
On branch master
nothing to commit, working tree clean
```

## 3. Modificando archivos

```bash
nano texto.txt
```
```text
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

```bash
git add texto.txt
```
```text
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   texto.txt
```

```bash
nano texto.txt
```

```bash
git status
```
```texto
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   texto.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt
```

```bash
git add texto.txt
```

```bash
git commit -m "Ampliada la explicación del texto"
```
```text
[master e896f0a] Ampliada la explicación del texto
 1 file changed, 2 insertions(+)
```

```bash
git status
```
```text
On branch master
nothing to commit, working tree clean
```

## 4. Información (git show y git log)

```bash
git commit -a -m "Nueva versión"
```

```bash
git show
```
```text
commit e896f0ad318a69eee0a57143825a10ea2c1a029c (HEAD -> master)
Author: Adrian S <adrian@gmail.com>
Date:   Thu Oct 8 13:21:51 2026 +0200

    Ampliada la explicación del texto

diff --git a/texto.txt b/texto.txt
index 15bf608..23c83ff 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,3 +1,5 @@
 uno
 dos
 tres
+cuatro
+cinco
:
commit e896f0ad318a69eee0a57143825a10ea2c1a029c (HEAD -> master)
Author: Adrian S <adrian@gmail.com>
Date:   Thu Oct 8 13:21:51 2026 +0200

    Ampliada la explicación del texto

diff --git a/texto.txt b/texto.txt
index 15bf608..23c83ff 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,3 +1,5 @@
 uno
 dos
 tres
+cuatro
+cinco
```

```bash
git log
```
```text
commit e896f0ad318a69eee0a57143825a10ea2c1a029c (HEAD -> master)
Author: Adrian S <adrian@gmail.com>
Date:   Thu Oct 8 13:21:51 2026 +0200

    Ampliada la explicación del texto

commit 32462a84581818333fe3145ccd7a41e0a6fecd26
Author: Adrian S <adrian@gmail.com>
Date:   Thu Oct 8 12:15:06 2026 +0200

    Añadido archivo texto.txt

commit 6b588d941df6cd879b99bea269413270ae1ad5d3
Author: Adrian S <adrian@gmail.com>
Date:   Thu Oct 8 11:59:11 2026 +0200
```

## 5. Diferencias (git diff)

```bash
nano texto.txt
```
```text
diff --git a/texto.txt b/texto.txt
index 23c83ff..bf98941 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,5 +1,5 @@
 uno
 dos
-tres
 cuatro
 cinco
+seis
```

```bash
git commit -a -m "Probando diff"
```
```text
[master dba2103] Probando diff
 1 file changed, 1 insertion(+), 1 deletion(-)
```

```bash
nano texto.txt
```

```bash
git diff
```
```text
diff --git a/texto.txt b/texto.txt
index bf98941..430cdae 100644
--- a/texto.txt
+++ b/texto.txt
@@ -3,3 +3,4 @@ dos
 cuatro
 cinco
 seis
+siete
```

## 6. Ignorar archivos (.gitignore)

```bash
ls -a
```
```text
./   .git/       Hola.class  importante~  temporal~
../  .gitignore  Hola.java   script.sh    texto.txt
```

```bash
git status
```
```text
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        Hola.java
        importante~

no changes added to commit (use "git add" and/or "git commit -a")
```

```bash
git add .
```

```bash
git commit -m "Añadidos fuentes en java y archivos importantes"
```
```text
[master e490b67] Añadidos fuentes en java y archivos importantes
 4 files changed, 13 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 Hola.java
 create mode 100644 importante~
```

```bash
git ls-tree --name-only -r HEAD
```
```text
.gitignore
Hola.java
importante~
script.sh
texto.txt
```

## 7. Tags y gestión de versiones (git tag y git checkout)

```bash
$ git show dba2103ae31cbf5ac065ad0ff6781a1d24202b2a
```
```text
commit dba2103ae31cbf5ac065ad0ff6781a1d24202b2a
Author: Adrian S <adrian@gmail.com>
Date:   Thu Oct 8 13:51:20 2026 +0200

    Probando diff

diff --git a/texto.txt b/texto.txt
index 23c83ff..bf98941 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,5 +1,5 @@
 uno
 dos
-tres
 cuatro
 cinco
+seis
```

```bash
git tag v0.7
```

```bash
git tag v0.3 32462a84581818333fe3145ccd7a41e0a6fecd26
```

```bash
git log --oneline
```
```text
e490b67 (HEAD -> master, tag: v0.7) Añadidos fuentes en java y archivos importantes
dba2103 Probando diff
e896f0a Ampliada la explicación del texto
32462a8 (tag: v0.3) Añadido archivo texto.txt
6b588d9 Confirmación inicial
```

```bash
git show v0.3
```
```text
commit 32462a84581818333fe3145ccd7a41e0a6fecd26 (tag: v0.3)
Author: Adrian S <adrian@gmail.com>
Date:   Thu Oct 8 12:15:06 2026 +0200

    Añadido archivo texto.txt

diff --git a/texto.txt b/texto.txt
new file mode 100644
index 0000000..15bf608
--- /dev/null
+++ b/texto.txt
@@ -0,0 +1,3 @@
+uno
+dos
+tres
```

```bash
git checkout v0.3
```
```text
Note: switching to 'v0.3'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 32462a8 Añadido archivo texto.txt
```

```bash
git checkout master
```
```text
Previous HEAD position was 32462a8 Añadido archivo texto.txt
Switched to branch 'master'
```

## 8. Ramas

```bash
git branch Prueba
```

```bash
git log --oneline
```
```text
e490b67 (HEAD -> master, tag: v0.7, Prueba) Añadidos fuentes en java y archivos importantes
dba2103 Probando diff
e896f0a Ampliada la explicación del texto
32462a8 (tag: v0.3) Añadido archivo texto.txt
6b588d9 Confirmación inicial
```

```bash
git branch
```
```text
  Prueba
* master
```

```bash
git switch Prueba
```
```text
Switched to branch 'Prueba'
```

```bash
git branch
```
```text
* Prueba
  master
```

```bash
git log --oneline
```
```text
e490b67 (HEAD -> Prueba, tag: v0.7, master) Añadidos fuentes en java y archivos importantes
dba2103 Probando diff
e896f0a Ampliada la explicación del texto
32462a8 (tag: v0.3) Añadido archivo texto.txt
6b588d9 Confirmación inicial
```

```bash
nano texto.txt
```

```bash
git commit -a -m "Rama para pruebas de código"
```
```text
[Prueba f4527e7] Rama para pruebas de código
 1 file changed, 1 insertion(+)
```

```bash
git log --oneline
```
```texto
f4527e7 (HEAD -> Prueba) Rama para pruebas de código
e490b67 (tag: v0.7, master) Añadidos fuentes en java y archivos importantes
dba2103 Probando diff
e896f0a Ampliada la explicación del texto
32462a8 (tag: v0.3) Añadido archivo texto.txt
6b588d9 Confirmación inicial
```

```bash
git commit -a -m "Llegan los Ents a Java"
```
```text
[Prueba b448f2a] Llegan los Ents a Java
 1 file changed, 1 insertion(+)
```

```bash
git tag v0.7-Ent-Release
```

```bash
git log --oneline
```
```text
b448f2a (HEAD -> Prueba, tag: v0.7-Ent-Release) Llegan los Ents a Java
f4527e7 Rama para pruebas de código
e490b67 (tag: v0.7, master) Añadidos fuentes en java y archivos importantes
dba2103 Probando diff
e896f0a Ampliada la explicación del texto
32462a8 (tag: v0.3) Añadido archivo texto.txt
6b588d9 Confirmación inicial
```

```bash
git switch master
```
```text
Switched to branch 'master'
```

```bash
cat Hola.java
```
```text
class Hola {
    public static void main(String[] args) {
        System.out.println("Welcome to the Java World");
    }
}
```

```bash
git merge Prueba
```
```text
Updating e490b67..b448f2a
Fast-forward
 Hola.java | 1 +
 texto.txt | 1 +
 2 files changed, 2 insertions(+)
```

## 9. Eliminar y quitar de seguimiento

```bash
git rm importante~
```
```text
rm 'importante~'
```

```bash
git commit -a -m "Exterminación de algo importante~"
```
```text
 [master 5695219] Exterminación de algo importante~
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 importante~
```

En caso de que quede algún archivo en seguimiento que se quiera quitar:
```bash
git reset HEAD *.class
```

## 10. Repositorios remotos: GitHub

```bash
git remote add origin https://github.com/Drin3780/MiPrueba
```

```bash
git branch -M main
```

```bash
git push -u origin main
```
```text
Enumerating objects: 32, done.
Counting objects: 100% (32/32), done.
Delta compression using up to 6 threads
Compressing objects: 100% (22/22), done.
Writing objects: 100% (30/30), 2.86 KiB | 418.00 KiB/s, done.
Total 30 (delta 6), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (6/6), done.
To https://github.com/Drin3780/MiPrueba
   37e211a..3b0478f  main -> main
branch 'main' set up to track 'origin/main'.
```

```bash
git push -u origin Prueba
```
```text
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
remote:
remote: Create a pull request for 'Prueba' on GitHub by visiting:
remote:      https://github.com/Drin3780/MiPrueba/pull/new/Prueba
remote:
To https://github.com/Drin3780/MiPrueba
 * [new branch]      Prueba -> Prueba
branch 'Prueba' set up to track 'origin/Prueba'.
```
