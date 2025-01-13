---
ospool:
  path: overview/account_setup/connect-access.md
---

# Log In to `uc.osg-htc.org` Access Points

**This guide is for users who were notified by a member of the OSG team that they 
will be using the "OSG Connect" Access Points. Do not go through the steps of this 
guide until advised to by a Research Computing Facilitator**

> To use the "OSG Connect" Access Points (`ap20.uc.osg-htc.org`, 
> `ap21.uc.osg-htc.org`), you must have first registered and have your account approved
> as described [here](../registration-and-login).

* If this is your first time logging in using OSG Connect, you'll need to first [set up multi factor authentication](#add-multi-factor-authentication-to-your-web-profile).

* If this is your first time logging in from your current device, 
you'll need to [add an SSH key to your web profile](#add-a-public-ssh-key-to-your-web-profile).

* If you've already set up an SSH key on your current device, you are ready to [log in](#log-in)!

## Log In

If you have recently [set up multi factor authentication](#add-multi-factor-authentication-to-your-web-profile)
or [set up an SSH key for your current device](#add-a-public-ssh-key-to-your-web-profile), 
please wait 15 minutes before trying to log in.

### For Mac, Linux, or newer versions of Windows

Open a terminal and type the following command, where you replace `your_osg_connect_username` and `your_osg_login_node`
with the appropriate values for your account: 

    ssh your_osg_connect_username@your_osg_login_node

It will ask for the passphrase for your ssh key (if you set one), then for 
a "Verification code" which you should get by going to the TOTP client you 
used to set up multi factor authentication. After entering the six digit 
code, you should be logged in. 

Note that when you are typing your passphrase and verification code, your typing will 
NOT appear on the terminal, but the information is being entered! 

> ### Finding your account information
> 
> Before you can connect, you will need to know your username and which login node your account is assigned to. 
> You can find this information on your profile from the OSG Connect website.
> 
> 1. Go to [https://www.osgconnect.net](https://www.osgconnect.net) and sign in with your institution credentials that you used to request an account. 
> 
> 2. Click "Profile" in the top right corner.
> 
> 3. The box on the left side contains your login information. 
>    The login node address should be listed in the top right of this box.
>    The `UNIX User Name` on the left side of this box is your username.
> 
> ![Identify Login Node](../../assets/ap7-images/find_osgconnect_login_node.png "OSG Connect Profile")
> 

### For older versions of Windows

On older versions of Windows, you can use the [Putty program](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) to log in. 

<img src="../../assets/ap7-images/putty-screenshots.png" alt="PuTTY Intructions Screenshot">

1. Open the `PutTTY` program. If necessary, you can download PuTTY from the website here [PuTTY download page](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).

2. Type the address of your assigned login node as the hostname (see "Determine which login node to use" above).

3. In the left hand menu, click the "+" next to "SSH" to expand the menu.

4. Click "Auth" in the "SSH" menu.

5. Click "Browse" and specify the private key file you previously generated.

6. Return to "Session". Then   

   * Name your session 

   * Save session for future use    

7. Click "Open" to launch shell. Provide your ssh-key passphrase (created at Step 4 in PuTTYgen) when prompted to do so.

8. When prompted for a "Verification Code", go to the TOTP client you used to set up 
two-factor authentication, above, and enter the six digit code from the client into 
your PuTTY terminal prompt. 

The following video demonstrates the key generation and login process from the [Putty](https://www.youtube.com/watch?v=zk1uo1nA2HA&t=210s&ab_channel=OSG) 

## Add a public SSH key to your web profile

Log in to OSG Connect Access Points is via SSH key. To generate an SSH key pair, 
see [this guide](../generate-add-sshkey) and then proceed with the following steps. 

To add your public key to the OSG Connect log in node: 

1. Go to www.osgconnect.net and sign in with the institutional identity you used when requesting an OSG Connect account. 

2. Click "Profile" in the top right corner.

3. Click the "Edit Profile" button located after the user information in the left hand box.

4. Copy/paste the public key which is found in the `.pub` file into the "SSH Public Key" text box. 
The expected key is a single line, with three fields looking something like 
`ssh-rsa ASSFFSAF... user@host`. If you used the first set of key-generating 
instructions it is the content of `~/.ssh/id_rsa.pub` and for the second (using 
PuTTYgen), it is the content from step 7 above.

6. Click "Update Profile"

The key is now added to your profile in the OSG Connect website. This will automatically
be added to the login nodes within a couple hours.

> ### Can I Use Multiple Keys?
> Yes! If you want to log into OSG Connect from multiple computers, you can do so by generating
> a keypair on each computer you want to use, and then adding the public key to your OSG 
> Connect profile. 

## Add multi factor authentication to your web profile

Multi factor authentication means that you will use 2 different methods to authenticate
when you log in. The first factor is the ssh key you added above. The second factor
is a 6 digit code from one of your devices. OSGConnect uses the TOTP
(Time-based One-time Password) standard - any TOTP client should work. Some common
clients include:

  * [FreeOTP](https://freeotp.github.io/)
  * [Google Authenticator](https://en.wikipedia.org/wiki/Google_Authenticator)
  * [DUO](https://duo.com/product/multi-factor-authentication-mfa/authentication-methods/tokens-and-passcodes)

> TOTP clients are most commonly used from smartphones. If you do not have 
> a smartphone or are otherwise struggling to access or use a TOTP client, 
> please contact the facilitation team: support@osg-htc.org

Once you have a TOTP client, configure it to be used with OSG Connect: 

1. Go to [https://osgconnect.net](https://osgconnect.net) and sign in with the institutional identity you used when requesting an OSG Connect account. 

2. Click "Profile" in the top right corner.

3. Click the "Edit Profile" button located after the user information in the left hand box.

4. Check the "Set up Multi-Factor Authentication" at the bottom and hit Apply.

5. In the Multi-Factor Authentication box, follow the instructions (scan the QR code with your TOTP client)

**Important: after setting up multi-factor authentication using your TOTP client, you will 
need to wait 15 minutes before logging in.**

