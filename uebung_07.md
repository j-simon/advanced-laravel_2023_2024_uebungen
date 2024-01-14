**Übung 7:** Refactoring der Socialite Anmeldung

Ich habe mir überlegt, dass du den Code so ändern könntest,
dass er mir kein Dorn mehr im Auge ist. 

Die Vorraussetzungen dazu stehen über der Übung. 

Selbstverständlich bestehe ich nicht auf Gitlab als zusätzlichen Provider. 
Suche dir einfach irgendeinen Socialite Provider aus und implementiere diesen. 

Achte vor allem darauf, das Open-Closed-Prinzip einzuhalten.

**Lösung:**

1.
Vorarbeiten(Github Anmeldung) müssen vorhanden sein!!

2. 
Refactoring und Open-Closed Prinzip

Gitlab soll hinzukommen!!!!!

a)
Die Routes in web.php anpassen:

```
Route::get('auth/{provider}', ....);
Route::get('auth/{provider}/callback', ....);

```

b)
Im LoginController.php, die Methoden bekommen den Parameter für den Provider

```
handleProviderCallback($provider)
{
.. überall github durch $provider ersetzen ;-)
}

redirectToProvider($provider)
{
.. überall den String 'github' durch $provider ersetzen ;-)
}
```

c)
Gitlab Socialite installieren

```
composer require socialiteproviders/gitlab
```

d)
Gitlab als Provider hinzufügen:
config/services.php

```
    'gitlab' => [
        'client_id' => env('GITLAB_KEY'),
        'client_secret' => env('GITLAB_SECRET'),
        'redirect' => env('GITLAB_REDIRECT_URI')
    ],
```

e)
hier bei Gitlab eintragen, vorher dort einen Account anlegen:

https://gitlab.com/oauth/applications

und die Keys erzeugen lassen:

f)

In der .env Datei hinzufügen:
```
GITLAB_KEY="ec608a3984XXXXXfddb99994eaa5171b5a4ac46ff6bee5ca6b7bffd86f107813"
GITLAB_SECRET="b5e6f2650df0XXXXXX1598d9eb2935027353cea28f2c6c65ee9ab787c628ce4c"
GITLAB_REDIRECT_URI="http://advanced-laravel.test/auth/gitlab/callback"
```

g) einen weiteren Link zur Anmeldung über Gitlab in der login-view hinzufügen:
```
....
</form>

                    <a href="/auth/github">Login mit Github</a><br>
                    <a href="/auth/gitlab">Login mit Gitlab</a><br>
                </div>
            </div>
        </div>
    </div>
</div>
@endsection

```
**Test:**

http://advanced-laravel.test/login

Mit Gitlab anmelden!

