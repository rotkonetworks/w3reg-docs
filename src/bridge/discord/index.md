# Setting up Discord Bridge
1. Install `bbctl` binary by downloading from the server.
![Installing `bbctl`](assets/installing.png)

2. Set executable permission so that `bbctl` will be able to run.
![alt text](image.png)

3. Log in by supplying email and auth code sent to it. 
![alt text](image-2.png)

4. Start a Discord bot instance by tunning `./bbcth run sh-discordgo`
![alt text](image-3.png)

5. Log into [Element](app.element.io/#/login) with your Beeper account.
![alt text](image-4.png)

6. In order to find the bot, you need to click $+$, then *Start new chat*. Once you do, you shall see a chat whose domain ends with `beeper.com`. Select the *Discord Bridge Bot*. Then click Go.
![alt text](image-5.png)
![alt text](image-6.png)




## Creating server
In order to perform registration, it's necessary to create a channel

## Creating bot
It is necessary in order to 

1. Go to [Discord Dev Portal](https://discord.com/developers/applications) and click on *New Application*
    ![alt text](image-7.png)

2. Set a name to your server and accept the *Terms of Service*. Click on *Create*
    ![alt text](image-8.png)

    **note**: You may come across captcha challenges, which you have to complete in order to proceed.

    ![alt text](image-9.png)

## Adding bot to server
1. Go to [Discord Dev Portal](https://discord.com/developers/applications), choose your created bot for registrar.

2. Go to *Bots*, scroll down to *Privileged Gateway Intents*, and enable 
    - *Server Members intent*
    - *Message Content intent*

    ![alt text](image-10.png)

4. Go to *OAuth2*. Scroll down to *OAuth2 URL Generator*, and check Bot. Set permission as admin, se bot can actually use the server.
    ![alt text](image-11.png)
    ![alt text](image-12.png)

5. Go to the bottom in order to copy the generated URL and go to it in new tab.
    ![alt text](image-13.png)
    ![alt text](image-14.png)

6. Select the registrar server, click *Continue*, and confirm Admin permission.
    ![alt text](image-15.png)
    ![alt text](image-16.png)


