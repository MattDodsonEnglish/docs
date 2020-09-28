To edit the theme files mentioned here, use your text editor of choice. For example, you can use [Visual Studio Code ↗](https://code.visualstudio.com/) or [Sublime Text ↗](https://www.sublimetext.com/).

Once you finish making your changes, **zip** the theme files, and [upload](#theme-installation) the final zip file to Ghost.

---

- [Theme Installation](#theme-installation)
- [Create a New Content API Key](#create-a-new-content-api-key) (<span class='u-color-success u-font-small'>Required</span>)
- [Upload the routes.yaml File](#upload-the-routesyaml-file) (<span class='u-color-success u-font-small'>Required</span>)
- [Members / Subscription](#members--subscription)
  - [Edit Plans Features](#edit-plans-features)
  - [Remove ‘Log in’ and ‘Subscribe’ from Header](#remove-log-in-and-subscribe-from-header)
  - [Membership Troubleshooting Tips](#membership-troubleshooting-tips)
- [RTL (Right to Left)](#rtl)
- [Header Navigation](#navigation)
- [Header Tags Menu](#header-tags-menu)
- [Footer Navigation](#secondary-footer-navigation)
- [Search](#search)
- [Tags Page](#tags-page)
- [Authors Page](#authors-page)
- [Contact Page](#contact-page)
- [Disqus Comments](#disqus-comments)
  - [Disable Disqus](#disable-disqus)
- [CommentBox Comments](#commentbox-comments)
- [Commento Comments](#commento-comments)
- [Sidebar Authors](#sidebar-authors)
- [Article Page Author](#article-page-author)
- [Posts Per Page](#posts-per-page)
- [Syntax Highlighting](#syntax-highlighting)
- [Related Posts](#related-posts)
- [Google Analytics](#google-analytics)
- [Responsive Tables](#responsive-tables)
- [Social Sharing Icons](#social-sharing-icons)
- [Sidebar Social Media Icons](#sidebar-social-media-icons)
- [Update Favicon](#update-favicon)
- [Theme Translation](#theme-translation)
  - [Add New Language](#add-new-language)
  - [Edit Translation](#edit-translation)
- [Theme Deploy with GitHub Actions](#theme-deploy-with-github-actions)
- [Theme Development](#theme-development)
  - [Code Injection](#code-injection)
  - [Changing Colors with CSS Variables](#changing-colors-with-css-variables)
  - [Customize Images Height](#customize-images-height)
  - [Customize Logo Size](#customize-logo-size)
  - [Center Post Page](#center-post-page)
  - [Remove the ‘Public’, ‘Members’ and ‘Paid’ Labels from Post Card](#remove-the-public-members-and-paid-labels-from-post-card)
  - [Remove Date from All Posts](#remove-date-from-all-posts)
  - [Add New Sidebar Widget](#add-new-sidebar-widget)
  - [Zip Theme Files](#zip-theme-files)
- [Theme Update](#theme-update)

---

### Theme Installation

The first step is to unzip the downloaded package. Inside, you will find the zipped theme and a documentation file. Upload the theme to your blog with the following steps:

1. Log in to your Ghost website admin (*example.com/ghost*)
2. In the left-side menu of your admin, click **Design**
3. Scroll down to the **INSTALLED THEMES** section
4. Click **Upload a theme**
5. Select the theme file (*krabi.zip*)
6. Once uploaded, click on **Activate now** to activate the theme immediately. If you want to activate it later, click **Close**.

---

### Create a New Content API Key

In order for the theme search to work, make a new *Content API Key* by following the next steps.

In the left-side menu of your Ghost admin click **Integrations** then **+ add custom integration**.

![Add new Ghost Custom integrations](https://d33wubrfki0l68.cloudfront.net/9e0d6d92fc0ad220dd8b98b45b5cedd95f72e50e/b642d/images/docs/ghost/shared/custom-integrations/add.png)

Then, give the new integration a name, for example, *Search* and click **Create**.

![Name for the Ghost Custom integrations](https://d33wubrfki0l68.cloudfront.net/0533efbaff834bcc5b8dbe09a044313d3ecde050/8fcb0/images/docs/ghost/shared/custom-integrations/name.png)

Now, a new API Key is created, hover over it and the **Copy** button will appear, click on it to copy the Key to the clipboard.

![Copy Ghost Custom integrations Content API Key](https://d33wubrfki0l68.cloudfront.net/21a910012bd866b1d5ba907bbd6da0fb020795e1/48437/images/docs/ghost/shared/custom-integrations/key.png)

Next, click **Code injection** from the left-side admin menu.

Add the following code to the **Site Header** box after replacing the *`API_KEY`*  value with your API Key.

```shell
<script>
  var search_api_key = 'API_KEY';
</script>
```

To be like.

![Inject Ghost Custom integrations Content API Key](https://d33wubrfki0l68.cloudfront.net/d92bcb8fe79ebd91623fdd56cd834bce2ad9f0fd/ba80e/images/docs/ghost/shared/custom-integrations/inject.png)

Click **Save**.

---

### Upload the routes.yaml File

The `routes.yaml` file is required for members sign up and subscription flows.

To upload the file.

- Go to the Ghost admin **Labs** settings page (`/#/settings/labs`)
- Scroll down to the **Routes** section and click the **Upload routes YAML** button
- Select and upload the `routes.yaml` file inside the theme zip file

![Upload a routes file in Ghost](https://d33wubrfki0l68.cloudfront.net/8297fc840444d57d5ea249cc43f7cd349049f0fb/59cc6/images/docs/ghost/shared/upload-routes.pngg)

#### Note

- You need to upload the `routes.yaml` separately. Uploading the theme zip file is not enough.
- There is already a `routes.yaml` file uploaded to Ghost. This is the default one that comes with Ghost. We need to upload the theme one to override it.

---

### Members / Subscription

Make sure to [Upload the routes.yaml File](#upload-the-routesyaml-file).

Subscribers can be enabled via a checkbox on the **Labs** page (`Labs > MEMBERS (BETA)`), in your Ghost admin panel:

![enable subscribers](https://d33wubrfki0l68.cloudfront.net/2903312ada3f12d49f1d15c29cfbf324cf4ed3ae/4fcd3/images/docs/ghost/shared/enable-members.png)

Once enabled, different parts of the theme will appear:

- Login In and Subscribe buttons in the header
- Sidebar and Footer subscription forms
- Post page subscription form
- Call to action section in Post page to encourage visitors to subscribe if the post is set to Members only

If the user is already logged in, all the forms will be hidden automatically.

---

#### Edit Plans Features

To edit each plan features, edit the `partials/member-plans.hbs` file.

![Subscription plans in Krabi](https://d33wubrfki0l68.cloudfront.net/ad03e3379c817808600d2d2a8bd2bff4aa09d24b/e2241/images/docs/ghost/krabi/plans.png)

The free plan column will be visible to non logged in users when they visite the [`/subscribe/`](http://krabi.aspirethemes.com/subscribe/) page.

To remove this column, open the `partials/member-plans.hbs` file and remove lines from `2` to `17`.

---

If the user clicked the free plan button, he will be directed to the [`/signup/`](http://krabi.aspirethemes.com/signup/) page with an email and subscribe button.

![Subscription plans in Krabi](https://d33wubrfki0l68.cloudfront.net/2cab85bf195391d81bd116d8aabf2dc70fead2c8/45565/images/docs/ghost/krabi/signup-free.png)

---

If the user is logged and is trying to subscribe to a plan from his account page, the monthly and yearly plans will be only available.

![Subscription plans in Krabi](https://d33wubrfki0l68.cloudfront.net/caf957b1c8e2b1f54a0bdb993da57f8e20f035c2/1c326/images/docs/ghost/krabi/plans-compact.png)

---

#### Remove ‘Log In’ and ‘Subscribe’ from Header

Open the `partials/header.hbs` file and remove lines from `30` to `38`.

---

#### Membership Troubleshooting Tips

If for any reason the subscribe form does not work or there is an error message, you may check out the following tips:

- If you are self-hosting your website, make sure to set up the [mail config](https://ghost.org/docs/concepts/config/#mail). After doing that, restart your Ghost server.
- The website config URL should match the URL used to access the website. As described in the [Ghost docs](https://ghost.org/docs/concepts/config/#url).

*Enter the URL that is used to access your publication. If using a subpath, enter the full path, `https://example.com/blog/`. If using SSL, always enter the URL with `https://`.*

---

For more information about Members, connecting Stripe, and setting the package price, check the [official Ghost documentation](https://ghost.org/docs/members/introduction/).

---

### RTL

RTL means (Right to Left), so the theme can show content in languages that are written from right to left like Arabic or Hebrew.

To enable the RTL version, open the `default.hbs` file and change line ***10*** to be `{{> compiled/inline-css-rtl }}`.

![Krabi Ghost Theme Activate RTL](https://d33wubrfki0l68.cloudfront.net/44f2a8200f9544cfd5dd36c75e62378a0f38cc16/d57cd/images/docs/ghost/shared/inline-css-rtl.png)

Save the file and upload the theme to your Ghost blog.

---

### Navigation

You can add, edit, delete, and reorder menu links on your Ghost blog from the Navigation section in the admin area located at `ghost/#/settings/design`.

![Ghost navigation menu](https://d33wubrfki0l68.cloudfront.net/feae47e5c4b5855f19a193b572a72946ab6fe06c/f91da/images/docs/ghost/shared/navigation.png)

To include a static page on your navigation menu. First, type the name of the page as you'd like it to appear on your menu in the label field.

![Ghost label field](https://d33wubrfki0l68.cloudfront.net/9763dfb165f2472dc7606232b0d651c421ae44bc/35266/images/docs/ghost/shared/label-field.png)

Next, click on the **URL** field of the menu item and we can find that the blog URL is already auto-populate for us. We will need to add the page slug after the final **/**. Once satisfied with our page configurations. Clicking the blue **Save** button will add the page to the navigation menu.

---

### Header Tags Menu

The tags menu will automatically show all the blog tags in alphabetical order.

![Krabi Tags Menu](https://d33wubrfki0l68.cloudfront.net/ffa0a0d5de95c2b0703d2b124eec4eea9e17da71/6b4b5/images/docs/ghost/krabi/tags-menu.png)

If you want to remove the **Latest** tab, open the `partials/tags-list.hbs` file and remove lines from `7` to `9`.

If you want to remove this entire tags list, open the `default.hbs` and `default-wide.hbs` files and remove line `12` from both of them.

---

### Secondary Footer Navigation

Similar to the [Header Navigation](#navigation), we can add the footer navigation from the `SECONDARY NAVIGATION` section in Ghost admin.

---

### Search

Make sure to [Create a New Content API Key](#create-a-new-content-api-key).

The theme uses [ghostHunter](https://github.com/jamalneufeld/ghostHunter).

Search is done for the Post title and the content. Search only support Posts but not Pages.

The search supports German, Spanish, French, Portuguese, Italian, Finnish, Dutch, Turkish, and Danish.

---

### Tags Page

To create the Tags page:
- From the Ghost admin `Pages` section, create a new page and call it **Tags** for example
- From `Page settings`, choose the `Tags` template from the `Template` dropdown
- Publish the page
- To add the page to the navigation, please check the [Navigation](#navigation) section above

![Ghost Tags Page](https://d33wubrfki0l68.cloudfront.net/450bd467288a88b5b03edeaa1ea1c7845153a820/d0089/images/docs/ghost/shared/tags-page.png)

#### Note

If you are self-hosting your website, you may need to do a server restart. This will help show up the **Template** dropdown **Tags** option.

---

### Authors Page

To create the Authors page:

- Create a new page and call it **Authors** for example
- From `Page settings`, choose the `Authors` template from the `Template` dropdown
- Publish the page
- To add the page to the navigation, please check the [Navigation](#navigation) section above

![Ghost Authors Page](https://d33wubrfki0l68.cloudfront.net/a7bf2c78299358d7baf81cd1954dfa361dce1449/a9e44/images/docs/ghost/shared/authors-page.png)

#### Note

If you are self-hosting your website, you may need to do a server restart. This will help show up the **Template** dropdown **Authors** option.

---

### Contact Page

To create the Contact page:

- Create a new Page and call it **Contact** for example
- Add your content and the contact form code using [FORMSPREE](https://formspree.io/) as a service. Please check the code example below
- Publish the page
- To add the page to the navigation, please check the [Navigation](#navigation) section above

```html
<form action="https://formspree.io/your@email.com" method="POST">
  <input type="text" name="name" placeholder="Name">
  <input type="email" name="_replyto" placeholder="Email">
  <textarea name='message' placeholder="Message"></textarea>
  <input class='c-btn c-btn--small c-btn--active' type="submit" value="Send">
</form>
```

For more information, check the [How to Add a Contact Form to Your Ghost Blog](https://aspirethemes.com/blog/ghost-contact-form) blog post.

---

### Disqus Comments

Open `partials/disqus.hbs` file. Change the `aspirethemes-demos` value for the `disqus_shortname` variable to match your Disqus account shortname.

```js
var disqus_shortname = 'aspirethemes-demos';
```

So, if your Disqus shortname is `exampleone`, the final code above should be:

```js
var disqus_shortname = 'exampleone';
```

That’s all you need to set up Disqus from the theme side. If you get any issue that comments are unable to load. First, make sure you have [registered your website with Disqus (Step 1)](https://help.disqus.com/customer/portal/articles/466182-publisher-quick-start-guide)

And also check the [Disqus troubleshooting guide](https://help.disqus.com/customer/portal/articles/472007-i-m-receiving-the-message-%22we-were-unable-to-load-disqus-%22) if you still have issues.

---

#### Disable Disqus

If you want to disable Disqus comments. Open the `post.hbs` file and comment or delete the line contains the `{{> disqus}}` text (line `40`).

---

#### Show Comments for Signed-in Users Only

If you want to show the comments for signed-in users only, open the `post.hbs` file and replace line `40` (`{{> disqus}}`) replace with the following code.

```html
{{#if @labs.members}}
  {{#if @member}}
    {{> disqus}}
  {{/if}}
{{/if}}
```

You can read more about Ghost visibility choices at [Content visibility](https://ghost.org/docs/members/content-visibility/).

---

#### CommentBox Comments

To enable [CommentBox](https://commentbox.io) as a comments system, open `post.hbs` file and replace line *40* replace with `{{> commentbox}}`.

The next step is to create a commentbox account and then from the dashboard, create a new project by filling your site information, and then you will receive a *Project ID*.

Copy that *Project ID* and open `partials/commentbox.hbs` file and replace it with the `my-project-id` value. That's it.

---

#### Commento Comments

To enable [Commento](https://commento.io) as a comments system, open `post.hbs` file and replace line *40* replace with `{{> commento}}`.

The next step is to create a Commento account and then [register your domain](https://docs.commento.io/installation/self-hosting/register-your-website/) with it.

---

### Sidebar Authors

The sidebar Authors section shows `3` authors ordered by posts count.

To remove this section, open the `partials/sidebar.hbs` file and remove line `8` (`{{> sidebar-authors }}`).

---

### Article Page Author

The Article page will show the Author info in two places.

1. The top header under the title and near the social sharing icons.

To remove this, open the `partials/post-header.hbs` file and remove lines from `16` to `24` and lines from `26` to `27`.

2. Under the blog article content.

To remove this, open the `post.hbs` file and remove lines from `23` to `25`.

---

### Posts Per Page

You can control how many posts to show per page from the `package.json` file like this:

```js
"config": {
  "posts_per_page": 8
}
```

The theme default value is set to `{{include.postsPerPage}}` posts per page.

---

### Syntax Highlighting

You can add a fenced code block by placing triple backticks <code>```</code> before and after the code block. For example:

<pre>
```
pre {
  background-color: #f4f4f4;
  max-width: 100%;
  overflow: auto;
}
```
</pre>

Will produce the following gray look:

![Krabi Ghost Theme Syntax Highlighting](https://d33wubrfki0l68.cloudfront.net/88580a906fc67c5523b816d32ddd7405bfaacfdc/cc565/images/docs/ghost/krabi/syntax-highlighting-raw-output.png)

To <strong>highlight</strong> a code block. Add the language alias like `css` or `js` to the code block. For example, the CSS code in the previous example will wrap between <code>```css</code> and <code>```</code> as follows:

<pre>
```css
pre {
  background-color: #f4f4f4;
  max-width: 100%;
  overflow: auto;
}
```
</pre>

Will produce the following colored look:

![Krabi Ghost Theme Syntax Highlighting with prismjs](https://d33wubrfki0l68.cloudfront.net/0a46470bb950613ebefc3b896350ed96ac449b7e/3eb25/images/docs/ghost/krabi/syntax-highlighting-colored-output.png)

To add an **inline code**, you can wrap the text between two backticks <code>` `</code>, for example:

This inline code example `absolute="true"`

Will produce the following look:

![Krabi Ghost Theme Syntax Highlighting with prismjs](https://d33wubrfki0l68.cloudfront.net/7fea70125c63218db16b69acdd6d9a06ef308a92/a8d81/images/docs/ghost/krabi/syntax-highlighting-inline-output.png)

---

Krabi shipped with [Prism.js](http://prismjs.com/), a lightweight, robust, and elegant syntax highlighter.

The [initial Prism package](http://prismjs.com/download.html#themes=prism&languages=markup+css+clike+javascript) includes some languages like *Markup*, *CSS*, *C-like*, and *JavaScript*.

You can add and support more languages. For example, to add support for PHP:

Get the PHP component script from [Prism CDN](https://cdnjs.com/libraries/prism).

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.13.0/components/prism-php.js"></script>
```

Add the script to Ghost **Code Injection** *Site Footer* section. Click the **Save** button.

![Krabi Ghost Theme Syntax Highlighting Code Injection PHP Prism](https://d33wubrfki0l68.cloudfront.net/ae7c8002ea613fca55f21ad0823cda41dc83dec3/a288c/images/docs/ghost/shared/syntax-highlighting-code-injection.png)

---

### Related Posts

Related posts will be visible on the single post in case there are similar posts sharing the same tags.

Enabling the [Public API](#enable-the-ghost-public-api) required.

---

### Google Analytics

To integrate Google Analytics, I would recommend using [Google Analytics](https://ghost.org/integrations/google/) integration by Ghost.

---

### Responsive Tables

Responsive tables are required and essential for adding tabular content and allows tables to be scrolled horizontally. You can make any table responsive across all viewports by wrapping a `table` with `.responsive-table`, for example:

```html
<div class='responsive-table'>
  <table>
    ...
  </table>
</div>
```

---

### Social Sharing Icons

You can customize and update the post social media sharing icons from the `partials/share.hbs` theme file.

---

### Sidebar Social Media Icons

Sidebar social media links placed in the `partials/sidebar-social-icons.hbs` file.

The Ghost CMS supports adding Facebook and Twitter profile URLs from the admin panel. Go to **General > Social accounts** and add your URLs. This will update Facebook and Twitter URLs within the footer social media section.

![social-accounts](https://d33wubrfki0l68.cloudfront.net/3e76f93de7ae6b06126c7686e706673ec8ccac65/bdc4e/images/docs/ghost/shared/social-accounts.png)

For using other social accounts, the theme is using [Evil Icons](http://evil-icons.io/) to provide very simple and clean icons. Here you can find a list of the social media icons to use:

Facebook

```html
<span data-icon='ei-sc-facebook' data-size='s'></span>
```

GitHub

```html
<span data-icon='ei-sc-github' data-size='s'></span>
```

Instagram

```html
<span data-icon='ei-sc-instagram' data-size='s'></span>
```

LinkedIn

```html
<span data-icon='ei-sc-linkedin' data-size='s'></span>
```

Odnoklassniki

```html
<span data-icon='ei-sc-odnoklassniki' data-size='s'></span>
```

Pinterest

```html
<span data-icon='ei-sc-pinterest' data-size='s'></span>
```

Skype

```html
<span data-icon='ei-sc-skype' data-size='s'></span>
```

SoundCloud

```html
<span data-icon='ei-sc-soundcloud' data-size='s'></span>
```

Telegram

```html
<span data-icon='ei-sc-telegram' data-size='s'></span>
```

Tumblr

```html
<span data-icon='ei-sc-tumblr' data-size='s'></span>
```

Twitter

```html
<span data-icon='ei-sc-twitter' data-size='s'></span>
```

Vimeo

```html
<span data-icon='ei-sc-vimeo' data-size='s'></span>
```

VK

```html
<span data-icon='ei-sc-vk' data-size='s'></span>
```

Youtube

```html
<span data-icon='ei-sc-youtube' data-size='s'></span>
```

To edit or update other existed and static social links, for example, the Instagram code block:

```html
<li class='c-social-icons__item'>
  <a href='#' aria-label='Instagram' target='_blank' rel='noopener'>
    <span class='c-social-icons__icon' data-icon='ei-sc-instagram' data-size='s'></span>
  </a>

```

The code above contains the ICON code from the above list, the social media link (`a`) within a list element (`li`).

Next, replace your Instagram full URL with the link `href` value so if your Instagram URL is:

```html
https://www.instagram.com/ghost/
```

the new code will be:

```html
<li class='c-social-icons__item'>
  <a href='https://www.instagram.com/ghost/' aria-label='Instagram' target='_blank' rel='noopener'>
    <span class='c-social-icons__icon' data-icon='ei-sc-instagram' data-size='s'></span>
  </a>

```

If you want to completely remove Instagram, you can delete all the code block, the `li`, `a`, and the icon.

---

### Update Favicon

You can change the favicon in Ghost from the *Admin > General > PUBLICATION IDENTITY > Publication icon* from the Publication icon section.

![Update Ghost CMS favicon](https://d33wubrfki0l68.cloudfront.net/82380d584ef2c6cece40ca86f743915e0b192572/e48dd/images/docs/ghost/shared/update-favicon.png)

---

### Theme Translation

Krabi supports [Ghost i18n](https://themes.ghost.org/docs/i18n) and comes with **German**, **Italian**, **Spanish**, **French** **Finnish**, **Portuguese** **Dutch**, **Turkish** and **Danish** translation.

To use another available language than English, go to **Admin > General > PUBLICATION INFO > Publication Language** and enter the [*ISO Code*](https://www.w3schools.com/tags/ref_language_codes.asp).

- `da` for Danish
- `de` for Germany
- `du` for Dutch
- `en` for English
- `es` for Spanish
- `fi` for Finnish
- `fr` for French
- `it` for Italian
- `pt` for Portuguese
- `tr` for Turkish

![Ghost Publication Language Setting](https://d33wubrfki0l68.cloudfront.net/5f6de54875c4443eae6633a37f3ff5746a520c50/112db/images/docs/ghost/shared/publication-language.png)

---

#### Add New Language

To add a new language, follow the following steps:

- Create a new file under the theme `locales` folder with the language [ISO Code](https://www.w3schools.com/tags/ref_language_codes.asp) code. So, if the new language will be Arabic, the new file name will be `ar.json`
- Copy the `en.json` file content into your new file and start to translate as shown in the following section
- Go to **Admin > General > PUBLICATION INFO > Publication Language** and enter the language code which will be `ar` in this example

---

#### Edit Translation

To improve or edit a translation in a specific available language. You can open the language file under `locales` folder:

```sh
|____locales
| |____da.json
| |____de.json
| |____du.json
| |____en.json
| |____es.json
| |____fi.json
| |____fr.json
| |____it.json
| |____pt.json
| |____tr.json
```

For example, the Germany translation file will look like:

```json
{
  "Loading": "Wird geladen",
  "More Posts": "Weitere Artikel",

  "Recent Posts": "kürzliche Artikel",
  "Featured Posts": "Beliebte Beiträge",
  "Page Not Found": "Seite nicht gefunden",
  "You might also like": "Das könnte Sie auch interessieren:",
  "Latest": "Neueste",
  "Authors": "Autoren",
  "Navigation": "Navigation",
  "Published with {ghostLink} & {themeLink}": "Veröffentlicht mit {ghostLink} & {themeLink}",

  "Share on Twitter": "Auf Twitter teilen",
  "Share on Facebook": "Auf Facebook teilen",
  "Share on LinkedIn": "Auf LinkedIn teilen",
  "Share on Pinterest": "Auf Pinterest teilen",
  "Share via Email": "Per E-Mail teilen",
  "Copy link": "Link kopieren",
  "Link copied to clipboard": "Link in die Zwischenablage kopiert",

  "Search": "Suche",
  "Search {siteTitle}": "Suche {siteTitle}",
  "Type to Search": "Suchbegriff(e) eingeben",

  "Paid": "Bezahlt",
  "Members": "Mitglieder",
  "Public": "Öffentlichkeit",

  "Account": "Konto",
  "Log In": "Einloggen",
  "Log Out": "Ausloggen",
  "Continue": "Fortsetzen",
  "Subscribe": "Abonnieren",
  "Subscribe Now": "Abonniere jetzt",
  "Your email address": "Deine E-Mail-Adresse",
  "Please check your inbox and click the link to confirm your subscription.": "Bitte überprüfen Sie Ihren Posteingang und klicken Sie auf den Link, um Ihr Abonnement zu bestätigen.",
  "Please enter a valid email address!": "Bitte geben Sie eine gültige E-Mail-Adresse ein!",
  "An error occurred, please try again later.": "Ein Fehler ist aufgetreten. Bitte versuchen Sie es später erneut.",

  "You've successfully subscribed to {siteTitle}": "Sie haben {siteTitle} erfolgreich abonniert.",
  "Great! Next, complete checkout for full access to {siteTitle}": "Toll! Schließen Sie als Nächstes die Prüfung ab, um vollen Zugriff auf {siteTitle} zu erhalten.",
  "Welcome back! You've successfully signed in.": "Willkommen zurück! Sie haben sich erfolgreich angemeldet.",
  "Success! Your account is fully activated, you now have access to all content.": "Erfolg! Ihr Konto ist vollständig aktiviert, Sie haben nun Zugriff auf alle Inhalte.",
  "Success! Your billing info is updated.": "Erfolg! Ihre Zahlungsinformationen werden aktualisiert.",
  "Billing info update failed.": "Aktualisierung der Rechnungsinformationen fehlgeschlagen.",

  "Already have an account?": "Hast du schon ein Konto?",
  "Don't have an account yet?": "Sie haben noch keinen Account?",

  "This post is for paying subscribers only": "Dieser Beitrag ist nur für zahlende Abonnenten",
  "This post is for subscribers only": "Dieser Beitrag ist nur für Abonnenten",
  "This page is for paying subscribers only": "Diese Seite ist nur für zahlende Abonnenten",
  "This page is for subscribers only": "Dieser Seite ist nur für Abonnenten",

  "Join the newsletter to receive the latest updates in your inbox.": "Treten Sie dem Newsletter bei, um die neuesten Updates in Ihrem Posteingang zu erhalten",

  "Choose your subscription": "Wählen Sie Ihr Abonnement",
  "Unlock full access to {siteTitle} and see the entire library of members-only content & updates.": "Schalte den vollen Zugriff auf {siteTitle} frei und sieh dir die gesamte Bibliothek mit Inhalten und Updates nur für Mitglieder an.",
  "Subscribe to {siteTitle}": "Anmelden bei {siteTitle}",
  "Choose this plan": "Wählen Sie diesen Plan",
  "Monthly": "Monatlich",
  "Yearly": "Jährlich",

  "Welcome back!": "Willkommen zurück!",
  "Log Into your account again.": "Melden Sie sich erneut in Ihrem Konto an.",
  "Send login link": "Anmeldelink senden",

  "Nice, you're a subscriber!": "Schön, dass Sie Abonnent sind!",
  "Your subscription will expire on": "Ihr Abonnement läuft am ab",
  "Your plan": "Dein Plan",
  "Card": "Karte",
  "Expires": "Läuft ab",
  "Next bill date": "Nächstes Rechnungsdatum",
  "Edit billing info": "ERechnungsinformationen bearbeiten",
  "You have an active {siteTitle} account with access to all posts.": "Sie haben ein aktives {siteTitle} Konto mit Zugriff auf alle Posts.",
  "You're a subscriber to free members updates": "Sie sind Abonnent der kostenlosen Mitgliederaktualisierungen",
  "You are subscribed to free updates from {siteTitle}, but don't have a paid subscription to read all the posts.": "Sie haben kostenlose Updates von {siteTitle} abonniert, haben jedoch kein kostenpflichtiges Abonnement, um alle Beiträge zu lesen."
}
```

Each line consists of a left key (`"More Posts"`) and the right value (`"Mehr Artikel"`).

The key is plain English which exists in all translation files and **should not be** changed. You can only change the value.

If you have suggestions to improve the current translations or adding a new language. Please <a href='{{ site.mailto }}'>let me know</a>.

---

### Theme Deploy with GitHub Actions

Krabi comes integrated with the amazing [Deploy Ghost Theme ↗](https://github.com/marketplace/actions/deploy-ghost-theme) Github action.

![Krabi GitHub Actions](https://d33wubrfki0l68.cloudfront.net/471c52f5a99f853040e5334838c18dafc6a8f829/d792f/images/docs/ghost/krabi/github-actions.png)

I have written about this at [How to Deploy Your Ghost Theme Using Github Actions ↗](https://aspirethemes.com/blog/deploy-ghost-theme). All you need to do it to follow steps **1** and **2**.

---

### Theme Development

If you are a developer and need to do heavy customization work. The theme is using [Gulp](https://github.com/gulpjs/gulp) to compile [Sass](http://sass-lang.com/) and JavaScript. This improves the development flow and makes it much faster.

#### Note

Changing any `hbs` file, for example, the `post.hbs` file **does not** require being in a development mode with gulp running. Just edit the file in your preferred editor and upload it.

First, make sure you have [**Node.js**](https://nodejs.org/en/), [**npm**](https://www.npmjs.com/), [**Gulp CLI**](https://gulpjs.com/docs/en/getting-started/quick-start#install-the-gulp-command-line-utility), and [**Bower**](https://bower.io/#install-bower) installed. Check [My Current Setup](#my-current-setup).

Run the following command in the theme root directory to install *npm* and *bower* dependencies.

```sh
npm install
```

To start Gulp, run:

```sh
gulp
```

This will compile Sass and JavaScript files, and start watching changes as you edit files.

Gulp will produce two files:

- `assets/js/app.min.js`: The final main JavaScript file
- `partials/compiled/inline-css.hbs`: The final CSS file

It's recommended to avoid editing these files if you are working with Gulp. Instead, do customizations in `assets/sass` files for CSS or in `assets/js/app.js` for JavaScript. So, we can make sure the flow is going in the right direction and we never lost any changes.

---

#### My Current Setup

In case you are wondering what my current environment set up is. The packages version I use, check the following.

```bash
$ node -v
v10.16.0

$ npm -v
6.14.8

$ bower -v
1.8.8

$ gulp -v
CLI version: 2.2.0
Local version: 4.0.2
```

This environment works well for running Ghost and also for theme development.

I'm using macOS.

---

#### Code Injection

Another choice for customization is to use the Ghost **Code Injection** settings in Ghost admin. For a CSS example, you can use the following code to change the logo color and font size.

```html
<style>
  .c-logo__link {
    color: #4550E5;
    font-size: 32px;
  }
</style>
```

---

#### Changing Colors with CSS Variables

Using [Code Injection](#code-injection), you can change the theme colors with CSS Variables.

For the list of the available theme color variables, check out the `assets/sass/settings/colors.scss` theme file and it will be like the following.

```css
:root {
  --color-brand:   #5869DA;
  --color-white:   #FFFFFF;
  --color-dark:    #000C2D;
  --color-text:    #000C2D;
  --color-gray:    #687385;
  --color-error:   #CC3C64;
  --color-success: #07815C;
  --color-border:  rgba(0, 0, 0, .05);
  --color-border:  #EAECEE;

  --bg-color:      var(--color-white);
  --bg-gray:       #F5F7F9;
  --bg-dark:       #12245A;
  --bg-white:      var(--color-white);

  --color-code-inline: var(--color-text);
  --bg-tag-list: linear-gradient(to left, var(--bg-color), rgba(255, 255, 255, 0));
}
```

If you want for example to change the theme brand color and in this case, it will be `#5869DA`. You can copy the color variable to *Code Injection (Site Header)* and assign it with your new color like the following example.

```html
<style>
  :root {
    --color-brand: red;
  }
</style>
```

The result will be.

![Krabi Ghost Theme Changing Colors with CSS Variables](https://d33wubrfki0l68.cloudfront.net/f198fd98d9ad212631534236ecc9e2ab3bd7df50/025d6/images/docs/ghost/krabi/color-variables-change.png)

The color brand is used for buttons, links color, and links hover. In the above example, we changed the color to be `red`. You can override this for any other variable.

If, for example, you want to add another color that is not available in the available theme variables and wants to add another style to a new element. You can create a new variable and give it a name and value.

We can extend the previous example to add a new color for the logo color and assign that variable to the `.c-logo__link` class.

```html
<style>
  :root {
    --color-brand: red;
    --color-logo: blue;
  }

  .c-logo__link {
    color: var(--color-logo);
  }
</style>
```

The logo will then have a `blue` color.

![Krabi Ghost Theme Changing Colors with CSS Variables](https://d33wubrfki0l68.cloudfront.net/f45fb8685c4a862c4bad944312598f45777e1506/267a7/images/docs/ghost/krabi/color-variables-change-logo.png)

#### Customize Images Height

If you want to customize the height of the images on the home page and on the post page, you can use the following CSS code.

For the single post image. The theme default value is `56.25%`. You can change this value to match your preference.

```css
.c-post-image-wrap:after {
  padding-bottom: 56.25%;
}
```

For the homepage cards. The theme default value is also `56.25%`.

```css
.c-post-card__image-wrap {
  padding-top: 56.25%;
}
```

The full code in [Code Injection](#code-injection) would be:

```html
<style>
  .c-post-image-wrap:after {
    padding-bottom: 56.25%;
  }

  .c-post-card__image-wrap {
    padding-top: 56.25%;
  }
</style>
```

---

#### Customize Logo Size

If you are using an image as a logo instead of the site name and want to change the logo size you can use the following code.

```html
<style>
  .c-logo__img {
    max-width: 96px;
  }
</style>
```

The default value is `96px`, so you can increase this value to match your preference. If the loge image has a large white space around, make sure you trim that space to get good results.

---

#### Center Post Page

[![akash.at Post Content Center](https://d33wubrfki0l68.cloudfront.net/8b45d2c417a3b3f3c8fc635ee7b6e2f78ad107d7/d454b/images/docs/ghost/krabi/akash-post-center.png)](https://akash.at/how-coin-master-reimagined-slots/)

The method is being used at [akash.at ↗](https://akash.at/how-coin-master-reimagined-slots/)

To make the blog post content to be centered and remove the sidebar, you can do the following two steps.

1. Duplicate the `default.hbs` file and give it another name, for example, `default-post.hbs`. Then, remove lines from `19` to `21`.
2. In the `post.hbs` file, change the first line to `{{!< default-post}}`.

That’s all that you need to do and the post will be centered automatically.

In case you want to add a wide and full-width style to images, you can add the following CSS code to [Code Injection](#code-injection) *(Site Header)* section.

```html
<style>
  .kg-width-full {
    width: auto;
  }

  @media (min-width: 40em) {
    .kg-width-full .kg-image {
      max-width: 100vw;
      pointer-events: none;
    }
  }

  @media (min-width: 64em) {
    .kg-width-wide {
      width: 100vw;
      max-width: 1140px;
      padding-left: 40px;
      padding-right: 40px;
  }}
</style>
```

---

#### Remove the ‘Public’, ‘Members’ and ‘Paid’ Labels from Post Card

Open the `partials/post-card.hbs` file and remove lines from `23` to `29`.

---

#### Remove Date from All Posts

To remove the date from all posts, add the following CSS code to Ghost [Code Injection](#code-injection).

```html
<style>
  .c-teaser__date,
  .c-post-card__date,
  .c-post-header__date,
  .c-search-result__date {
    display: none;
  }
</style>
```

Click **Save**.

By order, this code will remove the date from the following.

- Sidebar postcard
- Home postcard
- Post page
- Search results

---

#### Add New Sidebar Widget

Suppose you want to add a new widget to the sidebar, use the following code as a skeleton for the widget.

To add it to the sidebar, copy and paste it in the `/partials/sidebar.hbs` theme file before line *9*.

```html
<div class='c-widget'>
  <div class='c-title-bar'>
    <h3 class='c-title-bar__title'>YOUR_TITLE</h3>
  </div>

  <div class='u-bg-white u-border u-border-radius u-p-32'>
    YOUR_CONTENT_HERE
  </div>
</div>
```

Here you have two content placeholders.

- *YOUR_TITLE*: Replace this with your widget title
- *YOUR_CONTENT_HERE*: Replace this with your widget content

If you don't want to add a title, your skeleton should be.

```html
<div class='c-widget'>
  <div class='u-bg-white u-border u-border-radius u-p-32'>
    YOUR_CONTENT_HERE
  </div>
</div>
```

---

#### Zip Theme Files

To create a clean and small theme package. You can exclude different directories using the following command line:

```sh
zip -r krabi.zip krabi -x '*node_modules*' '*bower_components*'
```

This will exclude *node_modules* and *bower_components* directories from the final zip file.

If you are [running gulp](#theme-development), you can type the `gulp zip` command to do this.

---

### Theme Update

You may be asking: How can I update my theme to the latest theme version?

There are two choices:

- Keep your current theme and only replace the changed files from the new version. You can find the changed files on the theme page [**Changelog**](/changelogs/krabi)
- Or, use the new version as a starting point and redo your theme changes and customizations

One thing to reduce the need for redoing customization is to use the [**Code Injection**](#code-injection) tool. This is very helpful for adding custom CSS and tracking code for example. So, it's always recommended to keep your custom CSS code with Code Injection.

---