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
window.webpackChunkdiscord_app.push([[Symbol()], {}, (x) => (wpRequire = x)]);
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

### Enable Staff Mode

Enables some hidden features and sets your client to staff mode.

<details>
<summary>Expand</summary>
 
This will trick your client into thinking that you are a staff member of Discord (by modifiying certain flags) and will also allow you to access the experiments tab, developer options, and more. (In these menus you can get unreleased Discord updates, emulate a different client, generate build overrides and more.)

```js
let wpRequire;
window.webpackChunkdiscord_app.push([[Symbol()], {}, (x) => (wpRequire = x)]);
let user = Object.values(wpRequire.c).find((x)=> x?.exports?.default?.getCurrentUser && x?.exports?.default?._dispatcher?._actionHandlers).exports.default
module = Object.values(user._dispatcher._actionHandlers._dependencyGraph.nodes);

user.getCurrentUser().flags |= 1;
module.find((x)=>x.name === "DeveloperExperimentStore").actionHandler["CONNECTION_OPEN"]();
try {module.find((x)=>x.name === "ExperimentStore").actionHandler["OVERLAY_INITIALIZE"]({user:{flags: 1}})} catch {}
module.find((x)=>x.name === "ExperimentStore").storeDidChange()
```
<br>

</details>
<br>

### Send Bot message

Makes clyde say whatever you want (only visible to you)

<details>
<summary>Expand</summary>

Bot tag code:
```js
let MESSAGE_TO_SEND = 'bobs';

(()=>{
    let wpRequire;
    window.webpackChunkdiscord_app.push([[Symbol()], {}, (x) => (wpRequire = x)]);
    let Flux;
    for (const module of Object.keys(wpRequire.c).map((x) => wpRequire.c[x].exports).filter((x) => x)) {
        if (module.default && module.default['sendBotMessage'] !== undefined) {
            ((mod)=>{
                mod.sendBotMessage(window.location.pathname.slice(10).split('/')[1], MESSAGE_TO_SEND)
            })(module.default)
        }      
    }
})()
```
<br>
</details>
<br>

### Bot Tag

Spoofs your Discord suffix to show that you have Discord's `BOT` tag. (Only visible to you.)

<details>
<summary>Expand</summary>

Bot tag code:
```js
let wpRequire;
window.webpackChunkdiscord_app.push([[Symbol()], {}, (x) => (wpRequire = x)]);
for (const module of Object.keys(wpRequire.c).map((x) => wpRequire.c[x].exports).filter((x) => x)) {
    if (module.default && module.default['getCurrentUser'] !== undefined)
        module.default.getCurrentUser().bot = true
}
```
<br>
</details>
<br>

### @@everyone bug

Sends @@everyone instead of @everyone (doesnt actually ping)

<details>
<summary>Expand</summary>

code:
```js
(()=>{
    let wpRequire;
    window.webpackChunkdiscord_app.push([[Symbol()], {}, (x) => (wpRequire = x)]);
    let Flux;
    for (const module of Object.keys(wpRequire.c).map((x) => wpRequire.c[x].exports).filter((x) => x)) {
        if (module['Store'] !== undefined && module['Dispatcher'] !== undefined) {
            ((Flux)=>{
                let getStore = (name) => { return Flux.Store.getAll().find(store => Flux.Store.prototype.getName.call(store) === name) }
                let role = Object.values(getStore("GuildStore").getGuild(getStore("SelectedGuildStore").getGuildId()).roles).at(-1)
                console.log(`<@&${role.id}>`)
            })(module.default)
        }      
    }
})()
```
<br>
</details>
<br>

### All roles (visual)

Visually gives you all roles in a server, this one is minified out of embaressment for how bad the code is.<br>
if it doesn't work, try it again (idk why but it works)

<details>
<summary>Expand</summary>

code:
```js
(()=>{let e,t,d,l;window.webpackChunkdiscord_app.push([[Symbol()],{},t=>e=t]);for(const r of Object.keys(e.c).map((t=>e.c[t].exports)).filter((e=>e)))r.default&&void 0!==r.default.getSelfMember&&(r.default,l=r.default),void 0!==r.Store&&void 0!==r.Dispatcher&&(e=>{let r=t=>e.Store.getAll().find((d=>e.Store.prototype.getName.call(d)===t));t=r("GuildStore").getGuild(r("SelectedGuildStore").getGuildId()),d=r("UserStore").getCurrentUser().id,Object.values(t.roles).forEach((e=>{l.getMembers(t.id).find((e=>e.userId==d)).roles.push(e.id)}))})(r.default)})();
```
<br>
</details>
<br>

### Create friend invite

Makes an invite to be your friend, like a server invite but when they accept it friends you instantly

<details>
<summary>Expand</summary>

friend invite code:
```js
let wpRequire;
window.webpackChunkdiscord_app.push([[Symbol()], {}, (x) => (wpRequire = x)]);
for (const module of Object.keys(wpRequire.c).map((x) => wpRequire.c[x].exports).filter((x) => x)) {
    if (module.default && module.default['createFriendInvite'] !== undefined)
        copy("https://discord.gg/" + (1, await module.default.createFriendInvite()).code)
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
