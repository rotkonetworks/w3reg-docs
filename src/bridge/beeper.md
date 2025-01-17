# Setting up Beeper Account

1. Visit [beeper.com](https://beeper.com) and download the client that matches your operating system.
    ![beeper.com website](assets/1-beeper.com.png)
    ![beeper download](assets/1-download-beeper.png)

2. Open the installed client. If you don't already have an account, you will be prompted to create one.
    ![First screen when run for first time](assets/2-beeper-first-screen.png)

3. Check your email inbox for a 6-digit verification code sent by Beeper. Enter the code to proceed.
    ![Verification code](assets/3-verifyCode.png)
    ![Email code](assets/3-emailCode.png)

4. Set up your username, first name, and last name to personalize your account.

5. Carefully review the provided instructions and details, including privacy policies and other important information.
    ![Things You Should Know](assets/5-thingsYouShouldKnow.png)
    ![Your Privacy](assets/5-yourPrivacy.png)

6. Copy the secret key displayed on your screen. This key is essential for encryption of your messages and ensuring account security.
    ![Copy secret key](assets/6-copySecretKey.png)

7. Paste the copied secret key into the required field to verify that it was correctly saved.
    ![Paste Secret Key](assets/7-pasteSecretKey.png)
    ![Secret Key Warning](assets/7-warning.png)

    **Warning**: If you fail to save your secret key, you might not be able to recover your messages in case you need to log back into your account.

    **Important**: Beeper does not store your recovery key on its servers.

8. You may be asked to sync your contacts by connecting your Google account. This step is optional and can be skipped if you prefer not to bridge messages with Google.

9. Select the apps you want to connect with Beeper. For this example, we'll set up Discord.
    ![Select Apps to be Integrated](assets/9-selectApps.png)
    ![Discord Connection String](assets/9-connectDiscord.png)

10. Log in to Discord through the web interface and authorize the Beeper app to access your account.
    ![Log into Discord](assets/10-logInDiscord.png)
    ![Discord Connected](assets/10-connected.png)

11. After completing the setup steps, follow the on-screen instructions until you reach the inbox interface.

Before you can fully use the platform, you’ll need to change your password for added security.

12. Open [Element](https://app.element.io/#/login), and click the *Edit* button next to *matrix.org*.
    ![Element Sign In](assets/12-elementSignIn.png)

13. Replace the HomeServer address with `beeper.com`.
    ![Beeper.com homeserver](assets/13-settingBeeperHomeServer.png)

14. Since Beeper does not provide a password during account creation, you must set one. Click on *Forgot password?*, and then enter the email address associated with your Beeper account.
    ![Entering Email](assets/14-enteringEmail.png)

15. Look for an email from Beeper containing a verification link. This link is needed to authorize the password reset.
    ![Check your Email prompt](assets/15-checkEmailPrompt.png)

16. Click the verification link in the email, and then select *Continue* on the following page.
    ![Verification link](assets/16-verifyLink.png)
    ![Verification page](assets/16-verificationPage.png)
    ![Email Validated](assets/16-emailValidated.png)

17. Return to the Element client, click *Next*, and set a new password for your account. Confirm by clicking *Continue*.
    ![Setting Password](assets/17-settingPassword.png)
    ![Password Reset](assets/17-pásswordReset.png)

Congratulations! Your Beeper account is now fully set up. You can proceed to connect additional platforms like Discord or Twitter/X through the available bridges.

- [Discord Bridge](discord.md)
- [X Bridge](twitter.md)

