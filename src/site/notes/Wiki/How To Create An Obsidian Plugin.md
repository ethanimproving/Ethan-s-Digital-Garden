---
{"dg-publish":true,"permalink":"/wiki/how-to-create-an-obsidian-plugin/","created":"","updated":""}
---


- [Unofficial Plugin Documentation](https://marcus.se.net/obsidian-plugin-docs/)
- [Unofficial Blogpost](https://phibr0.medium.com/how-to-create-your-own-obsidian-plugin-53f2d5d44046)
- [Obsidian API Docs](https://github.com/obsidianmd/obsidian-api/)
- [For Plugin Developers](https://publish.obsidian.md/hub/04+-+Guides%2C+Workflows%2C+%26+Courses/for+Plugin+Developers)
- Toggle the [Developer Tools](https://marcus.se.net/obsidian-plugin-docs/getting-started/plugin-anatomy#:~:text=To%20view%20the%20console%3A,in%20the%20Developer%20Tools%20window.) by pressing Ctrl+Shift+I
- [5 Ways To Add Breakpoints](https://dev.to/bytefish/5-ways-to-add-breakpoints-on-chrome-devtools-f28)

1. Clone the [official Sample Plugin](https://github.com/obsidianmd/obsidian-sample-plugin) from GitHub

![](https://i.imgur.com/7cF2sFH.png)

![](https://i.imgur.com/VJmRW4D.png)


```bash  
# Clone repo  
$ git clone https://github.com/obsidianmd/obsidian-sample-plugin.git  
# Install dependencies  
$ npm install
# Run in developer mode
$ npm run dev
# Compile Typescript into 1 main.js  
$ npm run build  
```

[Build Your First Obsidian Plugin](https://www.youtube.com/playlist?list=PLIDCb22ZUTBnMCbJa-st4PD5T3Olep078)

[How to create a plugin for Obsidian](https://www.youtube.com/watch?v=XaES2G3PVpg&t=656s)

[How to start making an Obsidian Plugin | EP1](https://www.youtube.com/watch?v=-SY2t2iOvG4)

# Test in Development Mode

There are ways to test your changes to an Obsidian plugin without having to compile it into a `main.js` file every time you make a change. One approach is to use the "[development mode](https://help.obsidian.md/Developers/Build+plugins)" feature of Obsidian, which allows you to load your plugin directly from the source code.

Here are the general steps to enable development mode for an Obsidian plugin:

1.  Open Obsidian and go to the "Community Plugins" settings page.
2.  Find the plugin you want to test and click the "Enable development mode" button.
3.  Open the Obsidian vault where you want to test the plugin.
4.  Clone the plugin's GitHub repository to your computer and navigate to the plugin's directory.
5.  Install the plugin's dependencies by running `npm install` in the plugin's directory.
6.  Run `npm run dev` to start the development server. This will compile the TypeScript code into JavaScript and watch for changes.
7.  In Obsidian, open the command palette (by pressing `Ctrl+Shift+P` on Windows or `Cmd+Shift+P` on Mac) and run the "Reload plugins" command.
8.  Your plugin should now be loaded from the source code, and any changes you make to the TypeScript code will be automatically compiled and reflected in Obsidian.

Note that some plugins may require additional configuration or setup to work in development mode, so you should refer to the plugin's documentation or ask for help in the plugin's GitHub repository or community forum if you encounter any issues.

# Debug Mobile Errors

> Failed to load plugin obsidian-timelines.


```bash
git submodule add https://github.com/KjellConnelly/obsidian-dev-tools.git .obsidian/plugins/obsidian-dev-tools
```

`app.js` is not the same as `main.js`. `app.js` is the main JavaScript file for the Capacitor framework, which is used by Obsidian to run the mobile app. It provides a bridge between the mobile platform and the web view that the Obsidian app runs in.

Revert back to previous commits until you find one that works.

_How to test plugins on Android_ I think you need to have ADB on your computer installed (I always had that installed; if the following directions don’t work without it, install it); on your android phone you have to enable ADB (it’s under developer settings [tap the build number three times to get these settings]); then connect the phone to your computer over USB; open chrome (or chromium based browser should also work) and type `chrome://inspect` in the browser. Open obsidian on your phone, then it should appear in the browser. You will have the console and the inspector like you have for desktop Obsidian

# Copy CSS

Copy HTML Element, and The CSS Used into a CodePen. Then slowly whittle down the CSS if it doesn't interfere with anything.

![](https://i.imgur.com/CKkRIPJ.png)
