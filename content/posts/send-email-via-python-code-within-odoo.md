---
title: Send email via python code within Odoo
subtitle: Easy way to integrate email in automated actions
category:
  - Tutorials
  - Examples
author: Ruben
date: 2022-07-13T17:43:36.926Z
featureImage: /uploads/mctaifsdfhvu7pj9ukmjzy.jpeg
---
Sometimes you way to send an email via code instead of using the Odoo’s built-in email functionality. I was able to the following python code snippet to achieve that.

```
mail_pool = env['mail.mail']
values={}

values.update({'subject': subject})
values.update({'email_to': 'example@email.com'})
values.update({'body_html': html})
#values.update({'body': record })
msg_id = mail_pool.create(values)
```

And then call send function of the mail.mail

```
if msg_id:
  mail_pool.send([msg_id])
```