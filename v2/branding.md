# Setting Custom Domain

## App Setup
To setup your own domain name and theme colors follow the below steps: 

- Login to panel using primary domain name given by vendor
- Click branding on left side menu
- Enter your domain name in desired space. ex: my.example.com
- Name your product, will be used in all communication emails
- Title will be displayed on brower window
- Choose theme for your website, It's color themes for popular websites.
- Done

## CNAME Setup

Login to your domain register and create an CNAME record for your domain point to `cname-sms.txtsms.me`

## Have you setup your CNAME?

You can test that your domain is setup correctly using `dig`:

```shell
dig @8.8.8.8 +short CNAME my.example.com
```