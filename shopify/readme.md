# Shopify

Before you can develop Shopify themes locally, there are a few prerequisites to take care of. Here are the steps you need to take before you can start working on your local Shopify development.

## 1. For Local Shopify Development, You Will Need to Install the Shopify Theme Kit
The Shopify Theme kit is the official command line created by Shopify. It can be used on machines running Windows, Linux, or macOS, and the setup is straightforward.

Automatic installation options include the following:

- For macOS and Linux, there's the option to install it with a simple script from the terminal. The script you will need is:

```shell
curl -s https://shopify.github.io/themekit/scripts/install.py | sudo python
```

- For macOS with Homebrew you'll need the following script is what you need:

```shell
brew tap shopify/shopify
brew install themekit
```

- For Windows with Chocolatey, you'll need this script:

```shell
choco install themekit
```

Manual installation options include the following:

- For Linux and macOS, you will need to find the Theme Kit binary specifically for the system you use, and download it. [You can find all available versions](https://shopify.dev/themes/tools/theme-kit) on the Shopify Github.
    - After that, you will run the md5 theme to compare checksums.
    - Then, with the binary on the path, preferably /usr/local/bin
    - Finally, test if it's working by running theme version

- For Windows, you will start by creating a new folder in C:\Program Files and name it Theme Kit
    - After that, download the Theme Kit, extract it, and copy it to that folder
    - Add C:\Program Files\Theme Kit to your PATH environment
    - Test whether the installation was successful by running theme in cmd.exe

Important Note: If you have any older versions of Theme Kit installed, uninstall the gem from previous versions first. You can do that with gem uninstall shopify-theme command. After that, you can update Theme Kit with theme update  -version=[version number]. You can find the [latest versions on Github](https://github.com/Shopify/themekit/releases).

## 2. Taking Care of API Credentials
The second step to enable local Shopify development involves connecting the local theme to your Shopify store. For that, you need API credentials: a key, password, and theme ID.

API credentials give Theme Kit access to your store and theme files you have in the store. To get API credentials, do the following:

- Log in to Your Store and Shopify Admin.
- Navigate to "Apps."
- Choose "Manage Private Apps" and after that "Create a new private app."
- Enter the title under "Private App Name."
- Add your email address under "Emergency Developer Email."
- In the Admin API section, navigate to "Theme templates and theme assets" and choose "Read and write access." Without this, you won't be able to get the right credentials.
- Finally, click on "Save."

A prompt will appear warning that you are about to generate a new set of API credentials that can be used with your store and urge you to keep them safe. Click "I understand, create the app." This will generate API credentials under the "Admin API" section.

## 3. Finding the Theme ID
Every Shopify Theme has its own ID number, and you need this number every time you want to connect an already existing theme to Shopify Theme Kit.

- The simplest way to get this number is to find it via the Theme Editor:
    - Go to your store, navigate to "Themes."
    - Choose the theme you want the ID from, click the button with 3 dots on the top right, and choose "Edit HTML/CSS" from the drop-down menu.
    - The theme number will appear in the URL: [https://your_store.myshopify.com/admin/themes/numberswillbehere](https://your_store.myshopify.com/admin/themes/numberswillbehere).
- You can also run a command in the Theme Kit that will list all the themes associated with the store, as well as their IDs:

```shell
theme get --list -p=[your-api-password] -s=[your-store.myshopify.com]
```

## 4. Downloading the Theme for Local Development
Now that you have everything you need to start local Shopify development, you will need to create a config.yml file. This file is the main connection between the local environment and your store's theme.

First you want to create a local directory and step into it. Use these commands:

Create a directory:

```shell
mkdir [your-theme-name]
```

Step into the directory:

```shell
cd [your-theme-name]
```

Once you're in the directory, run the following command to create a config file based on the theme ID and your credentials:

```shell
theme get --password=[your-api-password] --store=[your-store.myshopify.com] --themeid=[your-theme-id]
```

## 5. Creating a New Theme
If you want a completely new theme, you can create it in the directory of your choice. Note that the command you use for it will also upload a copy of the new theme to your store (you'll find it under the name you specify) and link the store theme and local directory theme via config.yml.

This is the command you need:

```shell
theme new --password=your-password --store=your-store.myshopify.com --name="New Blank Theme"
```

## 6. Pushing Updates to Your Theme
Finally, you want all changes you do in the local Shopify development environment to automatically be reflected on the theme in your Shopify store. To do that, navigate to your theme directory in the Theme Kit and run the command theme watch.

This will instruct Theme Kit to register any changes you make locally and push them to the theme. To disable this, type ctrl + c.

# Things to Consider When Choosing the Shopify Theme Kit

The Shopify Theme Kit is not a fully local Shopify development platform; you still need to connect to Shopify servers when you compile and render Liquid. Yet, the Theme Kit is the best option to get as close to local development as possible.

If you want a fully offline Shopify development option, it's best to look at Motifmate.com, which provides a true offline environment. Be aware, however, that Motifmate is not maintained by Shopify, which could result in bugs and errors in your theme.

Need Help?
Need help with custom Shopify theme development?  Contact our experts today - we are one of the highest rated Shopify experts in the world.

# My Shopify Store

- URL: dev-sibs-store.myshopify.com
- Login: dev-sibs-store.myshopify.com/admin