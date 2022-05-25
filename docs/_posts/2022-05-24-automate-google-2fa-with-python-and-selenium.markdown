---
layout: post
title:  "Automate Google 2FA with Python and Selenium"
date:   2022-05-24 22:55:38 -0700
categories: Selenium
---
# Automate Google 2FA with Python and Selenium

Are you tired of do Google 2FA login every time in Selenium? Most people should have **Google prompts** as their default 2FA option, which can’t be automated since we can’t let our script to tap **Confirm** on the phone. Fortunately there is a way to automate the login workflow. Here is the tutorial that may be able to help you. First of all, let see the script running:

![Selenium Automation](/images/2022-05-24-automate-google-2fa-with-python-and-selenium/2fa.gif)

### Pre-requisite:
* Python 3
* Selenium
* Google Authenticator App

### Install Google Authenticator
Google Authenticator App generates 2-Step Verification codes on your phone. It’s available on both [iOS](https://apps.apple.com/us/app/google-authenticator/id388497605) and [Android](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2&hl=en_US&gl=US) app store.

![Google Authenticator](/images/2022-05-24-automate-google-2fa-with-python-and-selenium/google-authenticator-app.jpeg)

### Get verification codes with Google Authenticator
There is an official guide on how to [Turn on 2-Step Verification](https://support.google.com/accounts/answer/185839?hl=en&co=GENIE.Platform%3DDesktop#zippy=%2Cuse-google-authenticator-or-other-verification-code-apps), if you haven’t turned it on, please refer to the guide.

After enabling 2-Step Verification, there are multiple methods for verification. We will go with [Get verification codes with Google Authenticator](https://support.google.com/accounts/answer/1066447?hl=en&co=GENIE.Platform%3DAndroid).

1. Go to your [Google Account](http://myaccount.google.com/). At the top, click Security.
2. Under “Signing in to Google,” tap 2-Step Verification.
3. Under “Add more second steps to verify it’s you,” find “Authenticator app” and tap Set up.
4. Choose your Phone Type and click Next.
5. It will pop up a QR code, hold on, **DO NOT SCAN THE QR CODE**. Click **“CAN’T SCAN IT”**, and it will pop up a SECRET KEY:

![Secret Key](/images/2022-05-24-automate-google-2fa-with-python-and-selenium/authenticator-secret-key.png)

> This is the KEY we are gonna use in our automation, so please safely record it.

6. Follow the steps and complete setup on your phone.

### Generating OTP with Python
This part is quite straightforward. We will use [PyOTP](https://pyauth.github.io/pyotp/), a Python library for generating and verifying one-time passwords. We will use only two lines of code to generate OTP:

```py
from pyotp import *
totp = TOTP("<YOUR_SECRET_KEY>")
```

Pretty easy huh? Once got the OTP, you can just **send_keys(totp)** to the input field, then click **Next**. Done -> Successful Login!

**Full script:** https://gist.github.com/yixuanzhou/9ad2ce1cf087344623066f4fdcd4feb8



