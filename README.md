# PulumiOktaApplicationSetupATIPLCourse
A java program to setup Okta resources using pulumi.

First of all, create a new Okta Developer account at https://developer.okta.com/signup/.

Now open a terminal in your repository location and type in the following commands:
pulumi config set okta:orgName XXXXXX
pulumi config set okta:baseUrl YYYYYY


Where XXXXXX is the organization name of your brand new Okta organization. The name can be found in the top right side of your Okta dev page, and shopuld be something similar to dev-12345678
YYYYYY should be okta.com

Then, create a new Okta token in this way: https://developer.okta.com/docs/guides/create-an-api-token/main/. Remember to copy the token created this way.
pulumi config set --secret okta:apiToken ZZZZZZ
Where ZZZZZZ is the token you copied before. --secret will encrypt the token passed in.

Now, in the App.java file substitute "ApplicationName" in the OAuth builder with your desired application name.
You can now substitute the User builder params to customize the user that will be used later on to log in with the Okta sign in widget in the Angular SPA. Pay attention to the .email() option of the builder. Here an exesting email is advised to be used in order to activate him properly through e-mail verification. A non-active user will not be able to log-in with the Okta sing0in widget in the angular spa.
Alternatively, the user can be activated by the okta console admin, going under Directory > People. The select the desired user and press the button "Set Password & Activate". A tempory password will be chosen that will allow him to sign in one time only. At the first user sign in, a new password selection will be asked to the user.

Now, you can execute the command pulumi preview to see the modifications that will be done. If they are correct you can execute the command pulumi up to finalize them.

Now verify the mail that arrived to you e-mail account in order to activate the user or skip this passage if you activated the user by the admin console.
