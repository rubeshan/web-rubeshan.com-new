---
optimized_image: https://www.cloudways.com/blog/wp-content/uploads/Email-Hosting-Small-Business.jpg
title: "Odoo: Automated actions - Send email via Python code"
category:
  - Tutorials
featureImage: /uploads/social_default_image.png
layout: post
author: Ruben
date: 2021-08-10 14:44:23
paginate: false
subtitle: This tutotial will show you how to send email via python code. Mostly
  used in the Server actions such as Automated action, or Scheduled actions in
  Odoo.
tags:
  - email
  - odoo
  - automated
  - action
image: https://www.cloudways.com/blog/wp-content/uploads/Email-Hosting-Small-Business.jpg
description: Odoo has a built-in function to send email. We will explore how we
  can utilize that to send an email.
---
Sending an email via python code is pretty straight forward. This is useful for someone who wants to customize their Odoo server actions. 

```python
#setup the HTML email boddy
html ="optional HTML tags to stylize the email body"
mail_pool = env['mail.mail']
#add the email subjects and other fields etc...
values={}
values.update({'subject': subject})
values.update({'email_to': 'send_to_this_email@example.com'})
values.update({'body_html': html})
msg_id = mail_pool.create(values)

# And then call send function of the mail.mail,
if msg_id:
  mail_pool.send(\[msg_id])
```

Alternatively, you can use the built-in "Send Email" option in the action to do.

![](/uploads/screen-shot-2021-08-10-at-2.54.48-pm.png)

If you found this useful, please leave a comment below.