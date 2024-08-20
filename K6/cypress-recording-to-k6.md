## Recording a Cypress test and publishing it in the K6 

Ref : [https://medium.com/@gabriel.starczewski/using-cypress-to-automate-k6-scripts-recording-3c8f21616d3e](https://medium.com/@gabriel.starczewski/using-cypress-to-automate-k6-scripts-recording-3c8f21616d3e)

Pre-requisits:
- If using WSL and chrome is not installed : [https://github.com/pasindu-sandaruwan/my-cheatsheets/blob/main/Cypress/configure-chrome-in-wsl-for-cypress.md](configure-chrome-in-wsl-for-cypress.md)

---

1. Install CRX Extractor/Downloader for Chrome:  [Chrome Web Store ](https://chromewebstore.google.com/)

2. Download k6 recorder plugin for Chrome and save it to the disk
- While in the k6 recorder plugin page, click on the CRX extension and click on **Download as ZIP**

3. Unzip it from the downloaded location.

#### Code modifications

- Update the cypress.config.ts with the following configs
```
    reporter : "junit",
    chromeWebSecurity : false,
    reporterOptions : {
      "mochaFiles" : "results/TEST-demo.xml",
      "toConsole": true
    },
```

- Create a new folder as `plugins` in `/cypress/plugins`. Inside the plugins folder create a file `load_k6extension.js` and include the following code snippet inside the file
```
module.exports = (on, config) => {
    // `on` is used to hook into various events Cypress emits
    //`config` is the resolved Cypress config
    on('before:browser:launch', (browser, launchOptions) => {
      if (browser.isHeaded) {
        try {
          launchOptions.extensions.push('/home/pasindu-sandaruwan/Downloads');
        } catch (error) {
          console.log("extension not available"); //when in headless mode
        }
        return launchOptions;
      }
    })
  
  }
```

> ℹ️:  For the `launchOptions.extensions.push('/home/pasindu-sandaruwan/Downloads');` make sure to include the extracted zip file location of the **k6 recorder plugin**.

---

> 📓 Note
> 
> Trying to use the **VcXsrv** in Windows did not work. Therefore, had to use the Chrome in Cypress itself
