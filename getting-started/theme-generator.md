# Mediacurrent Theme Generator

The [Mediacurrent theme generator](https://github.com/mediacurrent/theme_generator_8) is a scaffolding tool that has evolved with the years to provide a production-ready Drupal 8 theme that is component-based ready out of the box.

## Working with the theme generator

The instructions below will get you up and running with the Theme Generator:

* Install NVM, NodeJS, & NPM
* In your Drupal 8 site, create a new directory for your theme \(i.e. `/themes/custom/my_awesome_theme`\)
* Inside **my\_awesome\_theme** \(or any whatever directory name you created, type the following command and press **Return**:

```bash
nvm install node && node -v > .nvmrc
```

_The command above will install the latest stable version of NodeJS and create a new hidden file in your project called `.nvmrc` where that version of Node will be declared as the default version for this project._

* Run the following command:

```bash
npm create yo mc-d8-theme
```

This command will begin the process to create your new theme.  Follow the on-screen instructions.

{% hint style="warning" %}
**WARNING:**  The theme's machine name should always match the directory you created in the first step above.
{% endhint %}

* After the theme has been successfully created, type the following commands:

```bash
npm install

npm run build && npm run watch
```

* Click the URL provided at the end of the last command's output \(http://localhost:3000\), to access Pattern Lab.

If you wish to access Pattern Lab using Drupal's URL, use the following path:

* http://**&lt;drupal-url&gt;**/themes/custom/**&lt;theme-name&gt;**/patternlab/index.html

_Update &lt;drupal-url&gt; and &lt;theme-name&gt; to match your environment_.

## Resources

Project: [https://github.com/mediacurrent/theme\_generator\_8](https://github.com/mediacurrent/theme_generator_8)

