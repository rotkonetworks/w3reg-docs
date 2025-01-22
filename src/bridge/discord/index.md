# Setting up Discord Bridge
1. Install `bbctl` binary by downloading from the server.
    ![Installing `bbctl`](assets/1.1-installing.webp)

2. Set executable permission so that `bbctl` will be able to run. `chmod +x ./bbctl`

3. Log in by supplying email and auth code sent to it. 
    ![alt text](assets/image-2.webp)

4. Start a Discord bot instance by tunning `./bbcth run sh-discordgo`
    ![alt text](assets/image-3.webp)

## Creating server
In order to perform registration, it's necessary to create a server and channel, so users can get the challenges.

1. Head to [Discord app](discord.com). Click on the `+` to the left. Choose *Create My Own*, no need to use a template. Select *Skip this question*
    ![alt text](assets/image-19.webp)
    ![alt text](assets/image-17.webp)
    ![alt text](assets/image-18.webp)

2. Set the server name, and proceed to create it
    ![alt text](assets/2.1-creatingGuild.webp)

3. Create a channel for users to get their challenges by clicking `+` beside *Text Channels*. Set channel name and proceed.
    ![alt text](assets/image-21.webp)
    ![alt text](assets/image-22.webp)

## Creating bot
It is necessary in order to 

1. Go to [Discord Dev Portal](https://discord.com/developers/applications) and click on *New Application*
    ![alt text](assets/image-7.webp)

2. Set a name to your server and accept the *Terms of Service*. Click on *Create*
    ![alt text](assets/image-8.webp)

    **note**: You may come across captcha challenges, which you have to complete in order to proceed.

    ![alt text](assets/image-9.webp)

## Adding bot to server
2. Go to *Bots*, scroll down to *Privileged Gateway Intents*, and enable 
    - *Server Members intent*
    - *Message Content intent*

    ![alt text](assets/image-10.webp)

4. Go to *OAuth2*. Scroll down to *OAuth2 URL Generator*, and check Bot. Set permission as admin, se bot can actually use the server.
    ![alt text](assets/image-11.webp)
    ![alt text](assets/image-12.webp)

    **Important**: Minimun required permissions for the bot:
    - *Send Messages*
    - *Create Public Threads*
    - *Send Messages in Threads*
    - *Read Message History*
    - *Add Reactions*

5. Go to the bottom in order to copy the generated URL and go to it in new tab.
    ![alt text](assets/image-13.webp)
    ![alt text](assets/image-14.webp)

6. Select the registrar server, click *Continue*, and confirm Admin permission.
    ![alt text](assets/image-15.webp)
    ![alt text](assets/image-16.webp)

## Bridging Discord server
w3reg API requires a Mastrix channel in order to pass the challenges. In  this case, it will be bridged through Discord

1. Log into [Element](app.element.io/#/login) with your Beeper account.
    ![alt text](assets/image-4.webp)

2. In order to find the bot, you need to click `+`, then *Start new chat*. Once you do, you shall see a chat whose domain ends with `beeper.com`. Select the *Discord Bridge Bot*. Then click Go.
    ![alt text](assets/image-5.webp)
    ![alt text](assets/image-6.webp)

A new chat will be created. To set up the bot, it's necessary to issue commands. Issue command `guilds` to get help on the chat, as well as to make sure the bot works.
    ![alt text](assets/image-23.webp)

3. Go to Discord new server. Guild/server ID can be gathered from URL. 
    ![alt text](assets/image-24.webp)

    URL format is `https://discord.com/channels/<guild_id>/<channel_id>`

4. Get back to Element Discord bot chat, and issue `guilds bridge <guild_id> --entire`
    ![alt text](assets/image-25.webp)

Congratulations! You have successfully a Discord server into Matrix.

