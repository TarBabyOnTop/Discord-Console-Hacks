# Discord Console Hacks ( actually maintained )

**USE EVERYTHING AT YOUR OWN RISK** <br>
Nobody has reported being banned from client-mods but this is against TOS. <br>
These are for educational purposes only. I do not condone nor take any responsibility for malicious use of these scripts. <br>
My personal client mod containing all of these hacks will be released soon (open source)

***
## How to use these Hacks
<details>
<summary>Expand</summary>
<br>
1. Press CTRL + SHIFT + I to toggle Developer Tools <br>
2. Click on "Console" if not already selected <br>
3. Paste the script in the command field <br>
4. Press enter <br>

<br>
</details>
<br>


### Obtain your Token
<details>
Copies your Token into the clipboard.<br>
**:warning: DO NOT GIVE THIS TO ANYONE. It grants full access to your account.**


Paste this into the console (while being logged in):

```js
let wpRequire;
let sym = Symbol()
let chunk = [[sym], {}, (x) => (wpRequire = x)];
window.webpackChunkdiscord_app.push(chunk);
window.webpackChunkdiscord_app.pop();
webpackChunkdiscord_app.splice(webpackChunkdiscord_app.indexOf(chunk), 1);
delete wpRequire.c[sym]
delete wpRequire.m[sym]
for (const module of Object.keys(wpRequire.c).map((x) => wpRequire.c[x].exports).filter((x) => x)) {
    if (module.default && module.default['getToken'] !== undefined)
        copy(module.default.getToken())
}
console.log('your token has been copied to your clipboard')
```

The token should be in your clipboard now.<br>
Please be careful when pasting the token, sending it to someone is like giving away your address, keys and passport/ID.<br>

</details>
<br>


### Bot Tag

Spoofs your Discord suffix to show that you have Discord's `BOT` tag. (Only visible to you.)

<details>
<summary>Expand</summary>

Bot tag code:
```js
let wpRequire;
let sym = Symbol()
let chunk = [[sym], {}, (x) => (wpRequire = x)];
window.webpackChunkdiscord_app.push(chunk);
window.webpackChunkdiscord_app.pop();
webpackChunkdiscord_app.splice(webpackChunkdiscord_app.indexOf(chunk), 1);
delete wpRequire.c[sym]
delete wpRequire.m[sym]
for (const module of Object.keys(wpRequire.c).map((x) => wpRequire.c[x].exports).filter((x) => x)) {
    if (module.default && module.default['getCurrentUser'] !== undefined)
        module.default.getCurrentUser().bot = true
}
```
<br>
</details>
<br>


### Easy Edit Mode

You can use this to make fake screenshots without having to use Inspect Element (CTRL + SHIFT + I) each time.

<details>
<summary>Expand</summary>

```js
document.designMode = 'on'
```

</details>
<br>

***
