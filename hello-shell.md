%title: Hello Shell
%author: Horváth Zsolt
%date: 2021-10-05

---

-> Scope <-

# Miről lesz szó?
* Kipróbáljuk a shell-t mint munkakörnyezet.

# Miről nem lesz szó?
* Konkrét Linux disztró mély megismeréséről.
* Komplikált shell szkriptelésről.
* Szerver üzemeltetésről.

---

-> Episode One: Terminológiák <-

---

-> Terminológiák: Shell <-

# Mi az a shell?

A shell egy felhasználói felület, amely elérhetővé teszi
számunkra az operációs rendszer funkcióit. A mi esetünkben
egy parancssor az interfész.

# Hol van a shell?

┌───────────────┐
│   UTILITIES   │
│ ┌───────────┐ │ ┌───┐  ┌─────┐
│ │   SHELL   │←┼─┤CLI│←─┤HUMAN│
│ │ ┌────────┐│ │ └───┘  └─────┘
│ │ │ KERNEL ││ │
│ │ └────────┘│ │
│ └───────────┘ │
└───────────────┘

# Mi történik most?

Egy mdp nevű programot (utility) indítottam a shell
segítségével ami megjeleníti ezt a prezentációt.

---

-> Terminológiák: Prompt <-

# Mi az a prompt?

A prompt (parancssor) ahova a parancsokat írjuk és egyéb
értékes információk megjelenítésére is szolgálhat.

# Miféle shell fut éppen?

```
echo $0
```

---

-> Terminológiák: Terminál Emulátor <-

# Mi az a terminál?

Egy elektrotechnikai vagy elektromechanikus eszköz amely
segítségével adatot vihetünk be vagy alakíthatunk át egy
számítógép segítségével.

# Mi az a terminál emulátor?

Egy program ami egy videó terminált emulál egy tőle
különböző vizuális környezetben.

# Ergo

Parancsokat adok a shell-nek a prompt segítségével egy
terminál emulátorban.

---

-> Episode Two: Navigáció, manipuláció <-

---

-> Navigáció, manipuláció: Billentyűparancsok  <-

- `Fel, le` - Előző parancsok közötti lépkedés.
- `Tab` - Begépelt parancs fájlnév kiegészítése.
- `Ctrl+L` - Képernyő törlése.
- `Ctrl+R` - "Reverse search".
- `Ctrl+C` - "Abort".

---

-> Navigáció, manipuláció: Munkakönyvtár <-

# Munkakönyvtár kiíratása

__pwd__ - "Print name of current/working directory."

# Fájlok és könyvtárak listázása

__ls__ - "List directory contents."

```
ls; ls -a; ls -l; ls -la; ls -lah
```

Options:

```
-a --all - "List all files"
-l - "Long listing format"
-h --human-readable - "Human readable"
```

---

-> Navigáció, manipuláció: Munkakönyvtár <-

# Munkakönyvtár megváltoztatása

__cd__ - "Change the shell working directory."

```
cd .; cd ..; cd ../.; cd ../..; cd; cd /;
```

---

-> Navigáció, manipuláció: Fájlok, könyvtárak <-

# Fájlok, könyvtárak létrehozása

__touch__ - "Change file timestamps."

```
touch file.txt
```

Vagy létrehozhatunk szövegszerkesztővel is mint pl a `nano`.

__mkdir__ - "Make directories."

```
mkdir folder; mkdir -p folder/archived/texts
```

Options:

```
-p --parents - "no error if existing, make parent
directories as needed"
```

---

-> Navigáció, manipuláció: Fájlok, könyvtárak <-

# Fájlok, könyvtárak másolása

__cp__ - "Copy SOURCE to DEST, or multiple SOURCE(s) to
DIRECTORY."

```
cp file.txt file1.txt
cp file.txt folder/
cp file.txt folder/changedfilename.txt
```

# Fájlok, könyvtárak mozgatása

__mv__ - "Rename SOURCE to DEST, or move SOURCE(s) to
DIRECTORY"

```
mv file.txt file1.txt
mv file.txt folder/
mv file.txt folder/changedfilename.txt
```

---

-> Navigáció, manipuláció: Fájlok, könyvtárak <-

# Fájlok, könyvtárak törlése

__rm__ - "Remove the FILE(s)."

```
rm file.txt; rm -r folder/archived/; rm file*
```

Options:

```
-r -R --recursive - "remove directories and their contents
recursively"
```

---

-> Episode Three: Programok, könyvtárstruktúra <-

---

-> Programok, könyvtárstruktúra: Önsegély <-

# Manual

`man` - "An interface to the system reference manuals"

```
man curl
```

# Apropos

`apropos` - "Search the manual page names and descriptions."

```
apropos url
```

# Tldr

`tldr` - "Displays simple help pages for command-line tools,
from the tldr-pages project."

```
tldr curl
```

# Cheat.sh

`cht.sh` - "The only cheat sheet you need."

```
cht.sh --shell
```

---

-> Programok, könyvtárstruktúra: Programok helye <-

A parancsok programok melyeket a shell futtat.
Az a program válik paranccsá amit futtathatóvá teszünk
és elérhetővé.

```
whereis ls
```

`\/bin` - Azokat a futtatható programokat tartalmazza amik
szükségesek a rendszernek.

`\/usr\/bin` - Elsődleges mappa a futtatható programok
részére. `whereis curl`

`\/usr\/local\/bin` - Futtatható programok melyeket nem egy
csomagkezelő segítségével telepítettünk. `whereis cht.sh`

`sbin` - Rendszergazda parancsai.

---

-> Programok, könyvtárstruktúra: Könyvtárstruktúra 1. <-

`\/` - Könyvtárfa origója.

`\/boot` - Rendszer indításához szükséges állományok helye.

`\/lib` - Osztott rendszerkönyvtárak, kernel modulok.

`\/dev` - Csatlakozott, csatolható különleges állományok pl.
partíciók, eszközök.

`\/etc` - Beállításfájlok, jelszavak, hálózati-beállítások,
etc.

`\/home` - Minden felhasznűló saját könyvtára.

---

-> Programok, könyvtárstruktúra: Könyvtárstruktúra 2. <-

`\/mnt` - Felcsatolt perifériák.

`\/proc` - Rendszer és folyamat információk. - 
`cat /proc/cpuinfo`

`\/root` - A rendszer gazdájának a könyvtára.

`\/tmp` - Ideiglenes adatok, pl. phpstan cache.

`\/usr` - Alkalmazások, rendszereszközök.

`\/var` - Változó adatokat tartalmazó állományok könyvtára
pl. levelek, logok.

---

-> Episode Four: Rendszeradminisztráció <-

---

-> Rendszeradminisztráció: Felhasználó kezelés <-

# Ki vagyok?

```
whoami
```

# Superuser jogok kérése
Rendszeradminisztrációs tevékenységeket superuser-ként 
hajthatunk végre, ezt a `sudo` paranccsal tehetjük meg ha
a sudo csoport tagjai vagyunk.

# Felhasználó teremtése

```
sudo adduser frank
```

---

-> Rendszeradminisztráció: Felhasználói adatok <-

# Felhasználók listája

```
cat /etc/passwd
```

Egy sor tartalma
username:password:userid:groupid:gecos:home:shell

```
sudo cat /etc/shadow
```

# Csoportok listája

```
cat /etc/group; sudo cat /etc/gshadow 
```

# Egy user csoportjai

```
groups hrvthzslt
```

---

-> Rendszeradminisztráció: Csoporthoz hozzáadás <-

# Új felhasználó superuserré tétele

```
sudo usermod -aG sudo frank
groups frank
```

# Bejelentkezés új superuserként

```
sudo login frank
exit
```

# Felhasználó pusztítása

```
sudo deluser --remove-home frank
```

---

-> Rendszeradminisztráció: Jogok <-

# Jogcsoportok

- owner - A fájl vagy könyvtár tulajdonosának jogai.
- group - A fájlhoz vagy könyvtárhoz csatolt csoport jogai.
- all users - Mindenki más.

# Jogok

- read - Olvasás joga.
- write - Manipuláció joga.
- execute - Futtatás joga.

# Listázás értelmezése

```
is directory? | owner | group | all users
d               rwx     r-x     r-x
```

---

-> Rendszeradminisztráció: Jogok menedzselése <-

# Jogok megváltoztatása

Jogok paraméterezése
┌───────────┬───────────┬───────────┐
│ jogok     │ bináris   │ decimális │ 
├───────────┼───────────┼───────────┤
│ rwx       │ 111       │ 7         │
│ rw-       │ 110       │ 6         │
│ r-x       │ 101       │ 5         │
│ r--       │ 100       │ 4         │
└───────────┴───────────┴───────────┘

```
chmod 755 workspace/
```

# Tulajdonos megváltoztatása

```
sudo chown frodo workspace/sandbox/
```

# Tulajdonos csoport megváltoztatása

```
sudo chgrp frodo workspace/sandbox/
```

# Állomány futtathatóvá tétele

```
chmod +x script.sh
```

---

-> Rendszeradminisztráció: Csomagok telepítése <-

# Csomag menedzselők

- APT (Advanced Packaging Tool) - Debian, Ubuntu, Mint
- RPM (Red Hat Package Manager) - RedHat
- Pacman - Arch

# Csomagok keresése

```
sudo apt update
apt search php7.4
```

# Csomag telepítése

```
apt search cmatrix
sudo apt install cmatrix
```

---

-> Episode Five: Parancsok összefűzése <-

---

-> Parancsok összefűzése: Operátorok 1. <-

# ;

Parancs futtatása parancs után.

```
echo "Hello" ; echo "World"
```

# &&

Parancs futtatása ha az előző futása sikeres volt.

```
echo "Hello" && cat workspace/ && echo "World" 
```

# ||

Parancs az előző sikertelensége esetén fut.

```
cat workspace/ || echo ":("
```

---

-> Parancsok összefűzése: Operátorok 2. <-

# &

Parancsok futása előzőre várakozás nélkül.

```
sleep 5 & echo "Sleeping"
```

# |

Parancs az előző kimenetének felhasználásával fut.

```
ls -lah | grep work
```

---

-> Parancsok összefűzése: Kimenet fájlba írása <-

# >

Parancs eredményének fájlba írása.

```
date | tr " " "-" > datelog.txt
```

# >>

Parancs eredményének fájlba írása új sorként.

```
date | tr " " "-" >> datelog.txt
```

---

-> Parancsok összefűzése: "Csővezeték" <-

Példamondat
> The quick brown fox jumps over the lazy dog

```
echo "The quick brown fox jumps over the lazy dog" >
brown-fox.txt
```

```
cat brown-fox.txt |
  tr -d ' ' |
  tr '[:upper:]' '[:lower:]' |
  grep . -o |
  sort -u |
  tr '\n' ' ' |
  sed 's/$/\n/' > alphabet.txt
```

```
cat alphabet.txt
```

---