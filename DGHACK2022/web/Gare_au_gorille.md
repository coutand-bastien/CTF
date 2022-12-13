# Un chasseur sachant chasser... 1/2

![alt text](./logo.png)

> Des analystes SOC du Ministère des Armées ont remarqué des flux suspects provenant de machines internes vers un site vitrine d'une entreprise. Pourtant ce site semble tout à fait légitime.
>
> Vous avez été mandaté par la Direction Générale de l'Armement pour mener l'enquête. Trouvez un moyen de reprendre partiellement le contrôle > du site web afin de trouver comment ce serveur joue un rôle dans l'infrastructure de l'acteur malveillant.
>
> Aucun fuzzing n'est nécessaire.
>
> Le flag se trouve sur le serveur à l'endroit permettant d'en savoir plus sur l'infrastructure de l'attaquant.

## Analysis

When you arrive at the site, you see a website of a burger diner. Nothing to report for the moment.

The first thing to do is to look at the site's functionalities, interactive elements of the pages. We find a page with a link to download the restaurant's menu. The request made is :

```
https://.../download.php?menu=menu_updated_09_11_2022.jpg
```

The second thing to do is to look at the service used to host the site. We can see in the request headers that the service used is **nginx/1.22.0**


## Resolution

we will test the **path traversal** technique. To do this we change the **?menu** parameter in the url with the download.php page.


```
https://.../download.php?menu=download.php
```

And then, BINGO! The download.php page is downloaded to our machine.

In the title, we are told "The flag is located on the server in the place where we can learn more about the attacker's infrastructure". So we go and get the nginx configuration file: /etc/nginx/nginx.conf.

```
https://.../download.php?menu=/etc/nginx/nginx.conf
```

This results in the flag : 
```DHACK{L3s_D0ux_Burg3r5_se_s0nt_f4it_pwn_:(}```