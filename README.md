# Mailster Template Activation
This script is required to connect a Mailster installation with the Envato API to download templates directly into Mailster. It allows to verify your buyers via your Envato app to download the package via the API.

## Preparation ##

To make this work you must have a working Mailster template zipped in you download package you upload to ThemeForest.
Check [the docs](https://docs.revaxarts.com/mailstertemplates/) how to prepare your template to work with Mailster.
It must be one zip file containing all your template files.
The zip file **must contain** the word **mailster** in it's name.


Working examples:
* your_template_name_for_mailster.zip
* mailster_template.zip
* mailster.zip

Not working examples:
* your_template_name.zip
* Mailster_template.zip
* mail_ster_template.zip


## Installation ##

* Copy the entire folder to an directory on your server which is accessible via http like `https://example.com/mailster-template-activation/`.
* Rename the `config.sample.php` to `config.php`.
* Go to the [Manage apps page](https://build.envato.com/my-apps/) on Envato and "Register a new app".
* Call it something like "Your Name Mailster templates".
* As "Required permissions" select "Download the user's purchased items"
* Enter as "Confirmation URL" the location of this script like `https://example.com/mailster-template-activation/`.
* Click on "Register App".
* Copy you "Secret Application Key" into the `config.php` file at `SECRET_APP_KEY`.
* Copy the "OAuth client ID" of your app into the `config.php` file at `CLIENT_ID`.

## Adding your Items ##

To add your items you need to modify the `config.php` file.

* replace the `999999` and the `111111` with the Envato item id of your template.
* change the values of `name`, `description`, `author`, ` author_url` and `version`

If you have multiple items just reproduce the steps for a new item in this array like

```
$items = array(

	999999 => array(
		'name' => 'Template name',
		'description' => 'This is the Description',
		'author' => 'the author',
		'author_profile' => 'https://example.com',
		'version' => '1.0',
	),

	111111 => array(
		'name' => 'Template name',
		'description' => 'This is the Description',
		'author' => 'the author',
		'author_profile' => 'https://example.com',
		'version' => '1.0',
	),

);
```

## Checking ##

To make sure everything is working set the `DEBUG` constant in the `config.php` to `true` and visit `https://example.com/mailster-template-activation/` in your browser.

Please check if your "Redirect URL" is equal to the one you have defined in your Envato App. If not uncomment the `REDIRECT_URL` constant in the `config.php` and past the exact URL. (watch for trailing slashes!)

**set the `DEBUG` value back to `false` to prevent output of sensitive information!**


## Make your templates visible to Mailster users ##

**Please use [this form](https://goo.gl/forms/8FyHTyZIn6huIsPF2) to submit your data**

For the final step it's required to send me some information about your templates so I can add them to the list of available templates.
For this information I need following info:

#### Name ####

The name of your template. Max 30 Characters. No HTML tags allowed

#### Image ####

The URL to an image of your template with dimensions of 300x225 (600x450 for HighDPI)

#### Description ####

A short description of your templates. Allowed HTML tags are `<a>` and `<strong>` (don't abuse)

#### URI ####

The website user can purchase the template. Mailster will add `utm_source=Mailster+Templates+Page`to this URL for Google Analytics tracking. Add the other parameters if needed.

#### Endpoint ####

Your endpoint you have defined about (`https://example.com/mailster-template-activation/`)

#### Envato Item ID ####

The ID of your template on the Envato marketplace.


**Please use [this form](https://goo.gl/forms/8FyHTyZIn6huIsPF2) to submit your data**

I will check your information and will update you when the information has been added. It will take up to 24 hours to be visible on the templates page of all users.

If you have more questions you can contact me via [Mailster.co](https://mailster.co/contact/) or via [my Envato profile](https://themeforest.net/user/revaxarts#contact).


## FAQ ##

#### Can I test the setup? ####

Unfortunately no. Envato doesn't provide a sandbox with their API so the only way to test it is to purchase your plugin with another account. If you're in contact with me I'm surely help you out and get a copy of one of your items for testing.


#### What if I didn't provide a valid zip file in my download package? ####

The user will get a notification like "This is not a valid Mailster template" and will maybe blame me for that issue. I'll remove your item from the list if you don't fix it.


#### I've updated my template. What's do I need to know? ####

Mailster checks for new version of the templates once a day. If the provided version from your endpoint is higher than the users version Mailster will show an update notification. Users need a valid purchase of your item to get the update!
Update the version number only when the update is available on ThemeForest. Otherwise people will get an older version.


#### What if my server is going down? ####

If Mailster cannot check for newer versions on your endpoint or your server responds with an unexpected result it will hide the template. As soon it's available again it will show up on the template section.


#### What if I manipulate the `index.php` file so buyers get malicious files on their site? ####

Mailster checks the content of the zip and removes all files which are not html, image files or a colors.json. If I notice such a behavior I will permanently ban you from the list of available templates.


#### Why do you offer this? Why do you make yourself more competition? ####

More competition means more value for buyers. At the end of the day they are who pay our bills. Other than that I know many developers and template designers have more things to offer that I can do. It's also a good advertisement for Mailster if your template offers support. It's win-win-win in my opinion.

