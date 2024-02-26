# Electron-Hello-World

## Introduction
Electron-Hello-World is a simple application built using Electron, an open-source framework developed by GitHub. This application serves as a basic template for starting Electron projects and demonstrates how to create a minimalistic "Hello World" desktop application.

## Features
- Displays a minimalist window with a "Hello, World!" message.
- Provides a foundation for building more complex Electron applications.

## Installation
1. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/your-username/Electron-Hello-World.git
   ```

2. Navigate into the project directory:
    ```bash
    cd Electron-Hello-World
    ```

3. Install dependencies using npm:
    ```bash
    npm install
    ```

## Usage
Once the installation is complete, you can run the Electron-Hello-World application by executing the following command in your terminal

```bash
npm start
```

This will launch the Electron application, displaying the "Hello, World!" message in a new window.

## Contributing
Contributions are welcome! If you have any ideas for improvements or new features, feel free to open an issue or submit a pull request.

## Licence
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.



# Important Commands and codes

## Required Tools
> Node, NPM

## Initialize Project
```bash
mkdir my-electron-app && cd my-electron-app
npm init
```

## Install Electron
```bash
npm install electron --save-dev
```

> Should add Gitignore for `Node.js`

## Run Electron App
**Update `"scripts"` on `package,json` as following**
```json
"scripts": {
    "start": "electron .", // Add this Line
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

**Start App**
```bash
npm run start
```

# Basic App Code
>`main.js`
```js
const { app, BrowserWindow } = require('electron');

function createWindow() {
    const win = new BrowserWindow({
        height: 600,
        width: 800,
        webPreferences: {
            nodeIntegration: true,
            enableRemoteModule: true
        },
        icon: path.join(__dirname, 'assets', 'img', 'icon.png'),
        title: 'My App',
    });

    win.setTitle('My App');
    win.loadFile('views/index.html');
    win.webContents.openDevTools();
}

app.whenReady().then(createWindow);

app.on('window-all-closed', () => {
    if (process.platform !== 'darwin') {
        app.quit();
    }
});

app.on('activate', () => {
    if (BrowserWindow.getAllWindows().length === 0) {
        createWindow();
    }
});
```

