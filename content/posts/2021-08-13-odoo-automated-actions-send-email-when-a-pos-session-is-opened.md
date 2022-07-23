---
optimized_image: /uploads/email_ss_1920.png
title: Odoo Automated Actions - Send email When a POS session is opened
category:
  - Examples
featureImage: /uploads/social_default_image.png
layout: post
author: Ruben
date: 2021-08-13 12:25:59
paginate: false
subtitle: As a business owner, you want to know when your staff opens a new POS
  session. Not only that, the details of the new session
tags:
  - odoo
  - automated
  - action
  - POS
image: /uploads/email_ss_1920.png
description: As a business owner, you want to know when your staff opens a new
  POS session. Not only that, the details of the new session
---
In this tutorial, we will look at just how we can inform the business owner or the Odoo Administrator when a new POS session is opened. 

You will create a new Automated action using the similar settings as below:

![](/assets/img/uploads/screen-shot-2021-08-13-at-11.50.41-am.png)

I set the "Trigger" to "On Update" because of the field we are comparing. If you want to compare other fields, you can use other suitable "Trigger".

When looking at the fine details, The "Before Update Domain" setting can be set as the following:

```
[["state","=","opening_control"]]
```

The Apply on Domain can be set as the following:

```
[["state","=","opened"]]
```

For simplicity, I set the "Action to do" to "Send Email" and will use the built-in email function to send the email. You can also [execute the python code to send the email. ](https://www.rubeshan.com/odoo-automated-actions-send-email-via-python-code/)

I setup a simple email template as below. Here are some of the values I care about:

![](/uploads/screen-shot-2021-08-13-at-12.36.40-pm.png)

POS New session opened email template

```
Starting balance: ${object.cash_register_balance_start}
Theoretical Closing Balance: ${object.cash_register_balance_end}
Difference :${object.cash_register_difference}
Order discounts : ${object.config_id.iface_discount}

Total Cash Transaction (pos.session) ${object.cash_register_total_entry_encoding}
Cash Journal (pos.session) ${object.cash_journal_id.name}
```

And that's it. Save it and test your Automated action. You will receive email alters with the details of the new POS session.