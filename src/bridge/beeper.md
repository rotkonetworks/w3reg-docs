# Setting up Beeper account

1. Head to beeper.com and install the client for your OS.
    ![beeper.com website](assets/1-beeper.com.png)
    ![beeper doenload](assets/1-download-beeper.png)

2. Launch the client. It will ask you to create an account if you don't have one. 
    ![First screen when ron for fist time](assets/2-beeper-first-screen.png)

3. Reviow your email inbox for a 6-digit verification code.
    ![erification code](assets/3-verifyCode.png)
    ![Enail code](assets/3-emailCode.png)

4. Create a username by specifying it, and setting first and last names.

5. Read and the rest of instructions carefully:
    ![Things You should Know](assets/5-thingsYouShouldKnow.png)
    ![Your Privacy](assets/5-yourPrivacy.png)

6. Copy and paste your secret key, which will be needed in order to decrypt messages. 
    ![Copy secret key](assets/6-copySecretKey.png)

7. Pasth given secret key, in order to make sure that it was correctly copied.
    ![Paste Secret Key](assets/7-pasteSecretKey.png)
    ![Secret Key Warning](assets/7-warning.png)

    **Warning**: If missed, you might not be able to recover messages when you log back in. 
    **Warning**: Recovery key will not be stored by beeper.com. 

8. You'll be prompted to sync your contacts by connecting your Google account. You can skip this step as it's not necessary in order to bridge messages.

9. Select all apps to be connected. In this case, we set up Discord. 
    ![Select Apps to be Integrated](assets/9-selectApps.png)
    ![Discord Connection String](assets/9-connectDiscord.png)

10. Log in to Discord Web interface, and authorize Beeper app.
    ![Log into Discord](assets/10-logInDiscord.png)
    ![Discord Connected](assets/10-connected.png)

11. Once completed the steps, go through the rest of the steps until you get to the imbox.

We've advanced a lot, but not done yet. A couple more steps, and you'll be done. In order to be able to use it, the password must be changed.

12. Go to [Element]([app.element.io](https://app.element.io/#/login)) and click *Edit*, besides *matrix.org*.
    ![Element Sign In](assets/12-elementSignIn.png)

13. Set HomeServer to `beeper.com`.
    ![Beeper.com homeserver](assets/13-settingBeeperHomeServer.png)

14. Since Beeper does not allow to set up password or give one, it must be set. Click *Forgot password?*, Then enter the email used to set up Beeper account.
    ![Entering Email](assets/14-enteringEmail.png)

15. Look for an email from Beeper containing verification link, to aotuorize passwork change..
    ![Check your Email prompt](assets/15-checkEmailPrompt.png)

16. Click on the link to verify your email. Then click *Continue*. 
    ![Verification link](assets/16-verifyLink.png)
    ![Verification page](assets/16-verificationPage.png)
    ![email Validated](assets/16-emailValidated.png)

17. Go back to Element and click *Next*. Then set a password. Clock *Continue*.
    ![settingPassword](assets/17-settingPassword.png)
    ![Password Reset](assets/17-pásswordReset.png)

-----

After all that, you'll finally be ready to hook up Discord or Twitter/X through the bridges!
- [Discord Bridge](discord.md)
- [X Bridge](twitter.md)
