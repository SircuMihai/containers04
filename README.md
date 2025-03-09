# Lucrare de laborator Nr4: 
Utilizarea containerelor ca medii de execuție.

# Scopul:
Familiarizarea cu comenzile de bază ale OS Debian/Ubuntu și comenzi de bază din Docker.

# Sarcina:
Pornind de la imaginea oficială a sistemului de operare Ubuntu, să se creeze un container care să conțină un server web Apache. Să se creeze o pagină web care să conțină textul "Hello, World!" și să se afișeze într-un browser.

# Executarea:

## Sa creat un repositoriu nou cu numele container04
[!image](./images/repositoriu.png)

## Se cloneaza repositoriul container04 pe masila locala
[!iamge](./images/clonare.png)

## Sa pornit aplicatia Docker Desktop
[!iamge](./images/docker.png)

## Executam comanda: docker run -ti -p 8000:80 --name containers04 ubuntu bash
[!image](./images/startDocker.png)
- docker run : creeaza și ruleaza un container;
- -ti : porneste un terminal interactiv, -t -> alocarea unui pseudo-TTY și -i -> intrare interactiva;
- -p 8000:80 : mapeaza portul 80 din container pe portul 8000 al hostului;
- --name containers04 : seteaza ca numele containerului sa fie containers04;
- ubuntu : seteaza imaginea Ubuntu ca baza a containerului;
- bash : deschide un shell Bash interactiv.

## In terminalul deschis executam urmatoarele comenzi:
### apt update
[!image](./images/ubuntuUpdate.png)
- comanda actualizaeza lista packetelor disponibile
### apt install apache2 -y
[!image](./images/ubuntuApache.png)
- comanda instaleaza serverul web apache2, -y -> accepta toate comfirmarile
### service apache2 start
[!image](./images/startApache.png)
- porneste serverul apache2, el automant, pentru server, seteaza ca port de rulare portul 80

## In bara de cautare a browserului dechidem: http://localhost:8000
[!image](./images/port8000.png)
### Ce vedeți?
- vedem pagina standarta a serverului web apache2

## Ne intoarcem in terminalul bash si executam urmatoarele comenzi:
### ls -l /var/www/html/
[!image](./images/accesulIndex.png)
- comanda afiseaza continutul directorului /var/www/html/, -l -> afiseaza pe lung continutul
### echo '<h1>Hello, World!</h1>' > /var/www/html/index.html
[!image](./images/echoIndex.png)
- comanda suprascrie continutul fisierului index.html, vezut precedent, cu un tag h1 cu continutul "Hello, World!"
### Trecem in browser si reimprospatam pagina deschisa cu http://localhost:8000
[!image](./images/helloWorld.png)
### Ce vedeți?
- vedem scrisul: Hello, World!

## In bash executam comenzile
### cd /etc/apache2/sites-enabled/
[!image](./images/directorApache2.png)
- comanda schimba directorul curent cu directorul /etc/apache2/sites-enabled/
### cat 000-default.conf
[!image](./images/catDefault.png)
- comanda afiseaza continutul fisierului 000-default.conf
### Ce vedeți pe ecran?
- pe ecran sa afisat informatii despre saitul pe protul 80

## Iesim din terminalul bash cu comanda: exit
[!image](./images/iesire.png)

## Afisam lista de containere din docker cu comanda: docker ps -a
[!image](./images/listaCont.png)

## Stergem containerul
[!image](./images/stergereCont.png)

# Concluzie
- Am învățat să creez un container care leagă portul gazdei de cel al containerului, astfel încât să pot accesa site-ul din browser. După ce am modificat fișierul index.html și am pornit Apache2, am văzut conținutul site-ului. Am observat că Apache2 trebuie să fie pornit pentru ca pagina web să funcționeze. De asemenea, folosind opțiunile -ti în comanda docker run, am putut rula toate comenzile în același terminal.