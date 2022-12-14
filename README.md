# Checkout Timer

**Custom Tag Template for Google Tag Manager**

Measuring checkout duration (to use as user timing in GA)

[![Template Status](https://img.shields.io/badge/Community%20Template%20Gallery%20Status-published-green)](https://tagmanager.google.com/gallery/#/owners/mbaersch/templates/checkout-timer) ![Repo Size](https://img.shields.io/github/repo-size/mbaersch/checkout-timer) ![License](https://img.shields.io/github/license/mbaersch/checkout-timer)

---

## How To Use
Use this template to create a new Tag that fires at (e-commerce) checkout and purchase events. The tag scans the dataLayer (backwards) for a ecommerce purchase or checkout object. 
If a checkout starts, a `checkoutTimerStart` event gets pushed to the dataLayer, including the `checkoutStart` as a variable. The timestamp is stored in localStorage. 

When a purchase event is found in the dataLayer and a start timestamp is available, the tag then sends another event (`checkoutTimerStop`) to the dataLayer, along with the following values: 

- ```checkoutStart```
- ```checkoutFinished```
- ```checkoutDuration```

### Settings
A checkout expires after 30 minutes without a transaction per default. If new checkout events occur after this timeout, a new timestamp is stored and the timer is reset. The default timeout (in minutes) can be changed in the tag settings. 

If any specific event names shall be uses instead of `checkoutTimerStart` and `checkoutTimerStop`, the default names can be changed as well in the settings.

### Using the dataLayer Information for Measurement 
The `checkoutDuration` can be used either as custom dimension in a separate event or `checkoutTimerStop` fires a timing hit in order to send the duration to GA.   
