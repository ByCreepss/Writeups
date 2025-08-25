# Challenge Content

This webpage : http://challenge01.root-me.org/web-serveur/ch20/

# Challenge Resolution

When we land on the webpage, we can see that we have an **“upload**” section, which is interesting since the name of the challenge is “File upload”, it is a common web vulnerability (documentation : https://owasp.org/www-community/vulnerabilities/Unrestricted_File_Upload)

Since the challenge tells us that we have to *upload PHP* code and since the challenge’s name is “*Double extension*”, we are going to write a really short piece of PHP code, hidden behind a .jpg (or .gif or .png) extension so that it bypasses the server’s verification :

**On a linux terminal :**

→ `nano image.php.jpg`

→ Write this :

```php
<?php
	system("cat ~./passwd")
?>
```

**Explanation** : the *system* function will execute what we passed to it, on the server, here : `cat ~/.passwd`, that reveals the content of the .passwd file located at the root of the application.

Once done, upload the file in the upload section and click on the URL where it has been stored. Congrats, you’ve got the password !
