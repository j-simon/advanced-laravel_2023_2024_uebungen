**Übung 1**: neue Class, neue Applikation

Damit wir richtig loslegen können, benötigen wir ein Laravel-Projekt.

Erstelle ein Projekt in einer Homestead Box. 

Verbinde die MySQL-Datenbank in Homestead mit deinem Projekt. 

Du kannst aber auch SQLite verwenden. 

Ich erstelle in meinem Übungsvideo ein Projekt mit dem Namen advanced-laravel. 

Lokal leite ich das Projekt auf die URL advanced-laravel.test. 

Dabei verwende ich absichtlich einen anderen Workflow als in der ersten Laravel Class, 
damit du verschiedene Herangehensweisen kennenlernen kannst. 

Versuche den gezeigten Code der Lektionen nachzuvollziehen und absolviere die Übungen. Dadurch sammelst du Erfahrung und gewöhnst dich ans Coding mit Laravel.

**Lösung:**

Anpassen der hosts Datei in Windows:

```

127.0.0.1		routinglaravel.test
127.0.0.1		advanced-laravel.test

```

Installation von Laravel per composer in der CMD im Ordner wo auch routinglaravel installiert wurde:

```

composer create-project laravel/laravel advanced-laravel

```
Laravel starten:

```

php artisan serve --port=80 --host=advanced-laravel.test

```

**Test:**

http://advanced-laravel.test


