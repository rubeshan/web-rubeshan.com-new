---
date: 2021-08-22 14:00:15
layout: post
title: Odoo - Automatically change the status of Rescue Session
subtitle: Let's use Odoo's server actions to update the status of a POS rescue sessions
description: When a POS rescue session is initiated in Odoo 14, you will not be
  able to easily close it. We will look at sumplifying that in this tutorial
image: /assets/img/uploads/pos-session1.png
optimized_image: /assets/img/uploads/pos-session1.png
category: tutorials
tags:
  - rescue
  - session
  - pos
  - odoo
author: Ruben
paginate: false
---
I haven't found an easy way to automatically close the POS rescue sessions in Odoo. In case you are new to this subject, rescue sessions are POS sessions that are initiated by Odoo to help you continue the business without any interruptions.

 Rescue sessions can be created for various reasons but for simplicity, lets consider the following. 

> For example, 
>
> Imagine you're running a business and you only have one physical POS terminal and on it and you have a regular POS session opened. When its time for you to close, you will begin by executing the required steps to close that session.
>
> During this time, a customer decides to walk in and you will need to serve them. Since the regular session is in "closing control" mode, open a new browser tab and navigate to the POS front-end URL. If you complete a transaction now, it will be assigned to a "Rescue Session".
>
> Later, once you are ready to open a new session, you will follow the standard procedure and proceed with the steps. Now, if you go to the list of POS sessions, you will see that, a regular session and a Rescue session will be open. Although, its fine to have both at the same time, you will have issues with accounting and tallying up the total.

To help with this issue, you can create the following Automated Actions which will help with that. See the example trigger below for guidance.

![](/assets/img/uploads/screen-shot-2021-08-22-at-2.35.35-pm.png)

Here are the values for ease of copy and paste.

**Title:** Automatically close Rescue sessions and post entries

**Trigger:** On Creation & Update

**Before update:** \["&",["rescue","=",False],\["state","=","opening_control"]]

**Apply on:** \["&",["state","=","opened"],\["rescue","=",False]]

**Action to do:** Execute Python Code

**Here is the python code to execute.**

```python
rescue_session = env['pos.session'].search([('state', '=', 'opening_control'),('name', 'ilike', 'RESCUE FOR POS')])
rescue_orders = env['pos.order'].search([('state', '=', 'paid'),('session_id', 'ilike', 'RESCUE FOR POS')])
if rescue_orders:
  rescue_orders.write({'state': 'done'})
  rescue_session.action_pos_session_closing_control()
```

\
If you find this useful, feel free to leave a comment below.