# Vue2+Electron



### 1.安装相关库

```
npm install electron
npm install vue-cli-plugin-electron-builder
```



### 2.配置

```
// package.json
{
	"scripts":{
		"build": "vue-cli-service electron:build",
    "dev": "vue-cli-service electron:serve",
	}
	...	
	"main":"background.js"
	...
}
```

### 3.创建窗口:background.js

```
'use strict'

import { app, BrowserWindow } from 'electron'
import { createProtocol } from 'vue-cli-plugin-electron-builder/lib'

var win;
var baseURL;

async function createWindow() {
    win = new BrowserWindow({
        width: 1400,
        height: 900,
        title: "简",
        webPreferences: {
            enableRemoteModule: true,
            webSecurity: false,
            nodeIntegration: true,
            contextIsolation: false,
            webviewTag:true,
        }
    })

    if (process.env.WEBPACK_DEV_SERVER_URL) {
        await win.loadURL(process.env.WEBPACK_DEV_SERVER_URL)
        baseURL = process.env.WEBPACK_DEV_SERVER_URL;
    } else {
        createProtocol('app')
        await win.loadURL('app://./index.html')
        baseURL = 'app://./index.html';
    }
}


app.on('activate', () => {
    // On macOS it's common to re-create a window in the app when the
    // dock icon is clicked and there are no other windows open.
    if (BrowserWindow.getAllWindows().length === 0) createWindow();
})
```

### 4.运行

```
npm run dev
```

### 5. 打包

```
npm run build
```

