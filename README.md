# Kwanko Default Tag for GTM setup guide

In this documentation, you'll find the detailed steps to easily setup the Kwanko Default Tag for GTM.

## Introduction

### What is it for ?

This tag goal is to make you compliant with our third party cookieless tracking feature called uniJS if you've not already installed it on your website.
It helps storing and sending the Kwanko click identifier usefull for the Kwanko tracking.

### When should I install it ?

As mentionned before, this tag might be usefull **only if you've NOT installed** our uniJS tracking library on your website, as uniJS library already handle that part. So if you don't have, it is optimal to install it in addition to our Kwanko universal conversion tag for GTM to guarantee better tracking results.

### What does it do ?

This tag does not fire any conversion or tracking events over Kwanko.
It is watching over incoming Kwanko **kwkuniv** param added by Kwanko in click links redirected to your website.
The value of this param will then be stored in a first party cookie called **kwku** and it's value automatically forwarded when a Kwanko conversion tag is fired on your website.
So this tag should be setup and triggered on all your website pages on page view to ensure optimal tracking.

## Setup steps

### Custom variable setup

First, you'll have to setup a specific custom JavaScript variable required in our template. This variable will dynamically generate an expiration date based on current date.

To add this variable, please refer to the **Variables > New** action in your GTM interface :

!["Creating new custom JS variable"](assets/img/kwanko_gtm_default_customjs_var_new.png "Creating new custom JS variable")

Then choose the Custom JavaScript variable type :

!["Choose custom JS variable type"](assets/img/kwanko_gtm_default_customjs_variable_setup.png "Choose custom JS variable type")

And paste the following JavaScript code snippet in the textarea field :
```
 function() {
   var cdate = new Date();
   cdate.setTime(cdate.getTime() + (60*24*60*60*1000));
   return cdate.toUTCString();
 }
```

!["Paste JavaScript snippet"](assets/img/kwanko_gtm_default_customjs_variable_code.png "Paste JavaScript snippet")

And save the variable with an appropriate name (ex: `expirationDate`).

### Search and add Kwanko template from the gallery

The first step is to add the Kwanko default tag template from the template gallery to your workspace.
In the "templates" tab, click on "Search Gallery" button and search for "Kwanko default tag" in the search bar.
!["Search & import Kwanko default tag from gallery"](assets/img/kwanko_gtm_gallery_search_detail.png "Search & import Kwanko default tag from gallery")

Follow the steps to add the template through the "Add to workspace" and "Add" button in the confirmation box.
From there, the imported template will be displayed in you workspace with the "gallery" flag.
!["Imported Kwanko default template"](assets/img/kwanko_default_tag_template_imported.png "Imported Kwanko default template")

### Create a new tag

Next step is to create a new Tag in your GTM workspace :
!["Creating new GTM Tag"](assets/img/kwango_gtm_default_newtag.png "Creating new GTM Tag")

### Tag configuration

Then you will have to configure your tag :
!["Kwanko Tag configuration"](assets/img/kwango_gtm_default_tag_configuration.png "Kwanko Tag Configuration")

And searching for the Kwanko default GTM template :
!["Choosing Kwanko Default Tag template"](assets/img/kwanko_gtm_default_tag_configuration_template.png "Choosing Kwanko Default Tag template")

Then you'll be asked to setup the expiration date variable.
You'll have to match it with the custom JavaScript variable you have setup previously.

!["Expiration date custom variable setup"](assets/img/kwanko_gtm_default_expirationdate_matching.png "Expiration date custom variable setup")
!["Matching custom JavaScript variable"](assets/img/kwanko_gtm_default_expirationdate_matching_bis.png "Matching custom JavaScript variable")

### Choose your custom trigger

Don't forget to associate a trigger rule that might be "All pages" for this tag (as it should be fired on each page of your website to be able to watch for incoming Kwanko tracking parameters) :

!["Kwanko Default Tag triggering configuration"](assets/img/kwanko_gtm_default_trigger.png "Kwanko Default Tag triggering configuration")


### Save, submit and publish your container

And that's it !
Congratulations, your Kwanko Default Tag is ready to be used.
