# How to Set Up Your Own Minecraft Server & Start Coding Plugins

## Goal
This guide will help you set up everything you need to start "vibe coding" your own custom Minecraft plugins - even if you've never programmed before! By the end, you'll have your own Minecraft server running with your custom plugin loaded.

## What You'll Need (with Download Links)

1. **Java LATEST (Java 17 or newer required, Java 21 recommended)**
   - [Download from Oracle](https://www.oracle.com/java/technologies/downloads/#jdk21-windows)
   - Choose "Windows x64 Installer"
   - Just click through the installer with default options
   - **After installing, open a new terminal and run:**
     ```
     java -version
     ```
     It should say `java version "17..."` or `java version "21..."`. If it says `1.8...` or Java 8, see the troubleshooting section below to update your environment variables or uninstall old Java versions.

2. **GitHub Desktop** - For downloading the project (no command line needed!)
   - [Download GitHub Desktop](https://desktop.github.com/)
   - Install and sign up for a free GitHub account if you don't have one

3. **Cursor IDE** - Where you'll write your plugin code
   - [Download Cursor](https://cursor.sh/)
   - This is like a smart notepad that helps you code

4. **Minecraft Java Edition** - To play on your server
   - [Buy/Download from Minecraft.net](https://www.minecraft.net/en-us/store/minecraft-java-bedrock-edition-pc)

## Step 1: Get the Plugin Project

1. Open GitHub Desktop
2. Click "Clone a repository from the Internet..."
3. Go to the "URL" tab
4. Paste this: `https://github.com/PaperMC/paperweight-test-plugin`
5. Choose where to save it (like `Documents\Minecraft-Plugins`)
6. Click "Clone"

## Step 2: Open the Project in Cursor

1. Open Cursor
2. Click "File" → "Open Folder"
3. Navigate to where you cloned the project (e.g., `Documents\Minecraft-Plugins\paperweight-test-plugin`)
4. Click "Select Folder"

## Step 3: Start the Server (First Time)

1. In Cursor, look for the file explorer on the left
2. Find and double-click `gradlew.bat`
3. A black window (terminal) will open and then close immediately—this is normal! This step does **not** start the server, it just prepares Gradle for use.
4. **Next, open a new terminal in Cursor (or VS Code, etc.) in your project folder.**
5. In the new terminal, type:
   ```
   .\gradlew.bat runServer
   ```
   (If you're on Mac/Linux, use `./gradlew runServer`)
6. **Wait patiently** - First time setup downloads everything needed (5-10 minutes)

The server will stop and ask you to accept the EULA.

## Step 4: Accept the Minecraft EULA

1. In Cursor's file explorer, open the `run` folder
2. Double-click `eula.txt`
3. Change `eula=false` to `eula=true`
4. Save the file (Ctrl+S)

## Step 5: Start Your Server!

1. Go back to the black terminal window
2. Type `runServer` and press Enter again
3. Wait for "Done!" message - your server is now running!

## Step 6: Connect to Your Server

1. Open Minecraft
2. Click "Multiplayer" → "Add Server"
3. Server Name: `My Local Server` (or anything you want)
4. Server Address: `localhost`
5. Click "Done" then double-click your server to join!

## Making Your First Plugin Change

Let's make a simple change to see it work:

1. In Cursor, navigate to: `src/main/java/io/papermc/paperweight/testplugin/TestPlugin.java`
2. Find the line that says `"Test plugin has loaded"`
3. Change it to something fun like `"My awesome plugin is starting!"`
4. Save the file (Ctrl+S)
5. In the terminal, press Ctrl+C to stop the server
6. Type `runServer` to start it again
7. Watch the console - you'll see your message!

## Let Friends Join Your Server

### Set Up Windows Firewall (One Time)

1. Press Windows key, type "Windows Security" and open it
2. Click "Firewall & network protection"
3. Click "Allow an app through firewall"
4. Click "Change settings" then "Allow another app..."
5. Click "Browse" and find Java:
   - Usually in `C:\Program Files\Java\jdk-21\bin\java.exe`
6. Click "Add" then check both "Private" and "Public"
7. Click "OK"

### Find Your IP Address

1. Press Windows key, type "cmd" and open Command Prompt
2. Type `ipconfig` and press Enter
3. Look for "IPv4 Address" - it'll be something like `192.168.1.100`
4. This is what your friends need!

### Friends Connect Using

- Server Address: `[Your IP]:25565` (example: `192.168.1.100:25565`)
- Make sure you're all on the same WiFi network!

## Troubleshooting

### Java 8 or Wrong Java Version Detected
If you see an error like:
```
Dependency requires at least JVM runtime version 17. This build uses a Java 8 JVM.
```
Or if `java -version` shows Java 8 (`1.8.0_xxx`), you need to update your system to use Java 17 or newer:

1. **Uninstall old Java versions:**
   - Open "Add or Remove Programs" (Windows key, search for it)
   - Search for "Java" and uninstall any Java 8 or older entries
2. **Set JAVA_HOME and update your Path:**
   - Open "Edit the system environment variables" > "Environment Variables"
   - Set `JAVA_HOME` to your new JDK path (e.g., `C:\Program Files\Java\jdk-21`)
   - In the `Path` variable, remove any lines pointing to old Java versions and add/move the new JDK's `bin` folder to the top
3. **Restart your computer and open a new terminal**
4. Run `java -version` again to confirm it shows Java 17 or 21

### "Outdated Server" Error
Your Minecraft version doesn't match. Check the server window for the version (like "1.21.6") and switch to that version in the Minecraft launcher.

### Server Won't Start
- Make sure you installed Java 21 (see above)
- Check that you saved the EULA file after changing it to true
- Try closing and reopening the terminal window

### Can't See Code Changes
Always stop the server (Ctrl+C) and restart it after making plugin changes!

## Next Steps

Now you're ready to start coding! Custom commands are a great place to begin. Here are some prompts you can type into Cursor as comments in your plugin files:

### 1. **Give Items Command**
**Prompt:** create a command called /gift that gives the player 64 diamonds when they type it
**Expected outcome:** Players can type `/gift` in chat and instantly receive a full stack of diamonds!

### 2. **Teleport Home Command**
**Prompt:** make a /home command that saves the player's current location and a /return command that teleports them back to it
**Expected outcome:** Players can set a home point with `/home` and teleport back anytime with `/return` - perfect for exploring!

### 3. **Fun Effects Command**
**Prompt:** create a /party command that gives the player speed, jump boost, and shoots fireworks around them
**Expected outcome:** Type `/party` for an instant celebration with superpowers and fireworks!

### 4. **Weather Control**
**Prompt:** add a /sunshine command that clears the weather and sets time to day
**Expected outcome:** Instantly turn any rainy night into a beautiful sunny day with `/sunshine`!

### 5. **Player Launcher**
**Prompt:** make a /launch command that launches the player 20 blocks into the air with no fall damage
**Expected outcome:** Type `/launch` to get shot into the sky safely - great for getting over mountains!

### How to Use These Prompts:

1. Open `PluginBrigadierCommand.java` in Cursor
2. Press Ctrl+L to open Cursor's chat (just like you're talking to me!)
3. Copy and paste one of the prompts above into the chat
4. Cursor will write the code for you - just click "Apply" when you like what you see
5. Save (Ctrl+S), restart your server, and try your new command!

### Pro Tips:
- Start with one command at a time
- Test each command before adding the next
- Change the command names to whatever you want (e.g., `/gift` → `/loot`)
- Modify the numbers in the suggestions (e.g., "64 diamonds" → "32 emeralds")
- Ask Cursor's chat to explain any code you don't understand!

## Tips for Success

- **Save Often**: Always Ctrl+S after making changes
- **Read Error Messages**: They usually tell you exactly what's wrong
- **Start Small**: Change one thing at a time
- **Have Fun**: There's no wrong way to experiment!

## Getting Help

- The server console shows helpful messages
- Cursor can explain code - just highlight and ask!
- Paper documentation: [papermc.io/docs](https://papermc.io/docs)

Remember: Every programmer started as a beginner. You've got this! 🎮✨ 