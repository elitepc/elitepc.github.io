---
layout: post
title: My New Post
date: 2023-03-04 18:01 +0000
---


draft from a previous post

* 17/01/2020

On January 17th a client of mine complained that they couldn't send email to some recipients in a recently configured cloud server.

On a closer inspection the problem was limited to sending inboxes that were managed by Office 365.

So on the same day I've started the usual ritual:

-> Inspect exim logs to see if there is any spam coming from my server
-> Fill out this form: https://sender.office.com
-> Fill out this form: https://support.microsoft.com/en-us/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75
-> Light a candle and pray for good luck
-> Forward the message to delist@messaging.microsoft.com (of course I couldn't foward the emails directly from the account that was having troubles... because... you know, I couldn't send emails to microsoft)

18/01/2020

On the 18th I've received feedback that I should go again to https://sender.office.com, submit the IP for unblock and then wait about 1 to 2 hours for the changes to propagate.

The feedback from send.office.com was that the IP was not blocked

I've forwarded multiple emails to their delist email so I have received multiple emails telling me to go to the same url in the following couple of days.

20/01/2020

On January 20th I've received feedback from that link:
- Not qualified for mitigation

I've had that response in the past with other IP Addresses and repeating the process has worked for me before, so I've repeated the process.

Same response:
- Not qualified for mitigation

So I've replied with the error messages I was getting and received a reply 2 hours later telling me that they will look into it along with the Escalations Team

21/01/2020

The day later I received a notification that the they implemented mitigation for my IP, it should just take 24 to 48 hours to propagate.

22/01/2020

24 hours later, the problem still persisted and I asked for a status update. I've received a reply that the mitigation would take 24 hours.

I've replied again on the same day explaining that this IP belongs to a cloud provider and that I have no control on what the previous tenant did. Telling them that this IP isn't in any public blacklist, them being the only provider blocking my emails.

The domain that was sending emails (normal work emails, contact vendors and clients through an email client (not automated)) had DKIM, DMARC and SPF setup.

On the same day I've received a response that was more informative. My IP is being filtered by their SmartScreen® Filter technology. And as it is always learning they can't manually whitelist any IP, but I could try:
- Format my email content better
- Have a opt-out button
- Ensure that my email lists (non existant for this server) are up to date
- Join the JMRP (Junk Mail Reporting Program) (which I can't because they don't send me the activation email)
- Join the SNDS (Smart Network Data services) (which I can't, same reason as above)
- Send the message to delist@messaging.microsoft.com
- Contact Office 365 with my admin account (non existant as I'm not managing anything related to office 365)
- Check more information about the error code in their pages - http://go.microsoft.com/fwlink/?LinkId=526653


With this information I kindly explain that if I can't send email to their servers how is that AI going to learn that my IP should not be blocked?

23/01/2020

I've received a reply that I should contact them through my admin center. I should also check the error codes page mentioned earlier and that if I have any troubles with JMRP/SNDS I should contact another email address.


Resolution: My provider was kind enough to change my IP Address. Good luck to the next unlucky person that gets that IP Address
