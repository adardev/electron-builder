first you have to create the nativefier app

you need npm and node :)

npm install -g nativefier

and then you create your app, with nativefier command

nativefier "yourapp" --name "yourname" --icon youricon.ico --single-instance --inject yourmedicine.css/js --disable-dev-tools

and thats it now you have your unpacked app

now we are going to use electron builder to generate the setup

first init the node app
npm init -y

then install electron builder with:
npm install --save-dev electron@25.7.0 electron-builder@26.0.12

now configure your package.json for release

this is an example:
{
  "name": "GitHub",
  "version": "1.0.0",
  "main": "resources/app/lib/main.js",
  "description": "GitHub",
  "author": "GitHub",
  "scripts": {
    "dist": "electron-builder"
  },
  "build": {
    "appId": "com.github.github",
    "productName": "GitHub",
    "directories": {
      "output": "dist"
    },
    "files": [
      "resources/**/*",
      "GitHub.exe"
    ],
    "win": {
      "target": "nsis",
      "icon": "resources/app/icon.ico"
    },
    "nsis": {
      "oneClick": false,
      "perMachine": true,
      "allowToChangeInstallationDirectory": true
    }
  },
  "devDependencies": {
    "electron": "^25.7.0",
    "electron-builder": "^26.0.12"
  }
}
