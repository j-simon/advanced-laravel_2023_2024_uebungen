**Übung 5:** Erste Schritte mit Laravels Login System

Hier ist wieder eine kleine Aufgabe, mit der ich dich testen möchte: 
Implementiere in deiner Laravel-Applikation, falls noch nicht geschehen, das Login-System. 

Wenn du dir bei einigen Punkten unsicher bist, kannst du natürlich in das Walkthrough schauen. 

Deine Aufgabe ist es, 
das Login-System zu nutzen. 

Auf dem Homescreen, also der URI /home, 
soll der Name des Nutzers angezeigt werden, wenn dieser angemeldet ist. 

Außerdem soll eine URI /secret, die den Text »gesicherter Bereich« wiedergibt, 
nur für angemeldete Nutzer aufrufbar sein.

**Lösung:**

1.

Das login system muss implementiert sein, siehe Tutorial "Schritt für Schritt1" und Video 8:43

Kapitel 4.1 Laravel Auth - in wenigen Schritten zum Login-System 

**wir starten direkt mit:**

a) composer require laravel/ui

b) php artisan ui vue --auth

c) php artisan migrate

d) npm run build

http://advanced-laravel.test

aufrufen, dort muss oben rechts Login als Link erscheinen!


2.

EInen user registrieren mit email Adresse, die email Adresse muss nicht existieren!

3.

die home route gibt es ja bereits aus der installation!

siehe web.php

```
use Illuminate\Support\Facades\Auth; // damit verschwindet die nervige Fehlermeldung von VS Code ;-)

Auth::routes();

Route::get('/home', [App\Http\Controllers\HomeController::class, 'index'])->name('home');
```



4. 
im Template home.blade.php:

auth()->user()->name hinzufügen!!

```
{{ __('Hi '.auth()->user()->name.'! You are logged in! ') }}
```

5. 

Die secret route einrichten in web.php:

```
Route::get('/secret',function(){
	return "gesicherter Bereich!";
})->middleware('auth');
```

6.
testen mit angemeldetem und abgemeldetem user!

**Test:**

http://advanced-laravel.test/secret

http://advanced-laravel.test/home



