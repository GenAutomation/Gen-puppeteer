
# Library <a href="https://genlogin.com" target="_blank">Genlogin API</a>

## Getting Started

Genlogin supports MacOS and Windows platforms.

### Installation
Download Genlogin app : <a href="https://genlogin.com/" target="_blank">Link here</a>
<!--`npm i genlogin`-->

For running example.js install puppeteer

`npm i puppeteer`



### Example

```js
const Genlogin = require('./Genlogin');
const puppeteer = require('puppeteer');

(async () => {
    const genlogin = new Genlogin("");
    const profile = (await genlogin.getProfiles(0, 1)).profiles[0];
    const  {wsEndpoint} = await genlogin.runProfile(profile.id)

    const browser =await puppeteer.connect({
        browserWSEndpoint: wsEndpoint,
        ignoreHTTPSErrors: true,
        defaultViewport: false
    });


    const page = await browser.newPage();
    await page.goto('https://genlogin.com');

    // await browser.close(); 
})();
```

### Running example:
`node example.js`
### Full GenLogin API
- Swagger: <a href="http://localhost:55550/api-docs" target="_blank">Link here</a> 
### 🐱 Bot / Fingerprint detection sites
Genlogin bypass anti-bot page like: Amazon, Ebay, Shoppee for data scraping work with native change fingerprint technology rewritten from the chromnium browser kernel without using javascript. Fingerprint data and device parameters are continuously updated to the latest Genlogin.





| Site check bot                                      | Resulut | Image                                         |
| --------------------------------------------------- | ------- | --------------------------------------------- |
| [Recaptcha-v3](https://recaptcha-demo.appspot.com/) | Pass    | ![](https://hackmd.io/_uploads/BkS90901T.png) |
| [Creepjs](https://abrahamjuliot.github.io/creepjs/) | Pass    | ![](https://hackmd.io/_uploads/r1ffn90JT.png) |
| [sannysoft](https://bot.sannysoft.com/)             | Pass    |  ![](https://hackmd.io/_uploads/ryuIyiCk6.png)|
| [Pixelscan](https://pixelscan.net/)                 | Pass    | ![](https://hackmd.io/_uploads/B13L29Ak6.png) |




### Methods:
LOCAL_URL = "http://localhost:55550/profiles"

- ### getProfiles(limit=1000,offset=0)
  - return { profiles :[...],pagination: [...]}
- ### getProfiles(id)
  - return { id: ..., user_id: ...,profile_data:{...},...}
- ### getWsEndpoint(id)
  - return { success: true, data: { wsEndpoint: 'xxx' } }
- ### runProfile(id)
  - return {success: true, wsEndpoint: 'xxx'}
- ### stopProfile(id)
  - return { success: true }
- ### getProfilesRunning()
  - return { success: true, data: [...] }

