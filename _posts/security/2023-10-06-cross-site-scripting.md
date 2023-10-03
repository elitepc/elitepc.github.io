---
layout: post
title: Cross-Site Scripting
date: 2023-10-06 18:01 +0000
tags: xss security programming javascript  
categories: security
---

In this post, you will learn more about cross-site scripting web vulnerability.

According to research conducted by PreciseSecurity, in 2019, nearly 40% of All Cyber Attacks were performed by using cross-site scripting (XSS)[1].

How it can be used to impact real systems and have some guidelines on how to deal with user data. Covering all possible attack vectors that stem from XSS is not in the scope of this article, but I’ll leave you with some links for you to learn more about this topic.

## What is XSS?
A cross-site scripting (XSS) attack takes advantage of 2 main points of how the internet and browsers work:

- Most websites need javascript to run properly
- The browser trusts javascript code in the pages that the user visits
- Knowing this, the goal of someone that’s trying to exploit these flaws is to insert malicious javascript code in web pages for the victims to execute.
- This kind of flaw has 2 main categories, Stored and Reflected.

### Stored
Where the vulnerability is permanently stored on the target servers. For example, if we can insert a script in a comment section, everyone seeing the comments will be attacked.

### Reflected
Where the vulnerability comes from an input, for example, a GET parameter. If we can get our victim to click on a malicious link with a GET parameter, that is being printed back on the webpage, we have a successful attack.

## The risk
Ok, security is fun to theorize about, but what’s the risk? As always, it depends on the type of web application, the existence of other existing vulnerabilities, the application visibility, and lots of other things. So it can range from the attacker being able to redirect users to other pages or to being able to steal authentication tokens from highly privileged users, rendering the login form useless.

Now you may be thinking: “Yea yea, that’s cool and all, but… give me real examples”.

### MySpace – The first cross-site scripting (XSS) Worm that infected more than 1 million users

The funniest case I’ve seen so far was exploited by Sammy Kambar. He was a MySpace user and noticed that the platform was vulnerable to this flaw and that he could execute javascript in his profile.

He thought that it would be a good idea to execute javascript on everyone that visited his profile, where, without their knowledge, they would send him a friend request and change their profile description to “but most of all, Samy is my hero” and the same code would be replicated in the visitor’s profile.

The result wasn’t what he anticipated, as this turned into a worm, as it grew exponentially. This was the first documented case of an XSS worm and it infected over 1 million profiles in 24 hours.

![Excerpt of the code on their profiles](/assets/img/post_images/220px-SamyIsMyHero.png)


## See this from his point of view:

<iframe width="420" height="315" src="http://www.youtube.com/embed/9yOjLV5wlIo" frameborder="0" allowfullscreen></iframe>

Ok, but that’s an old platform, it should be solved by now, right?

Nope, see:

- cross-site scripting (XSS) in CKEditor (June 2020) [[https://portswigger.net/daily-swig/underestimated-dangers-of-copy-and-paste-exposed](https://portswigger.net/daily-swig/underestimated-dangers-of-copy-and-paste-exposed)]
- cross-site scripting (XSS) in GraphQL (June 2020) [[https://portswigger.net/daily-swig/graphql-playground-devs-patch-longstanding-xss-vulnerability](https://portswigger.net/daily-swig/graphql-playground-devs-patch-longstanding-xss-vulnerability)]
- Some XSS vulnerabilities fixed on WordPress 5.4.2 (June 10, 2020) [[https://portswigger.net/daily-swig/wordpress-security-release-addresses-multiple-xss-vulnerabilities](https://portswigger.net/daily-swig/wordpress-security-release-addresses-multiple-xss-vulnerabilities)]
- XSS in TCExam (June 2020) [[https://portswigger.net/daily-swig/online-learning-platform-tcexam-marked-down-for-weak-web-security](https://portswigger.net/daily-swig/online-learning-platform-tcexam-marked-down-for-weak-web-security)]
- XSS in Google Voice browser extension (May 2020) [[https://portswigger.net/daily-swig/xss-vulnerability-uncovered-in-google-voice-browser-extension](https://portswigger.net/daily-swig/xss-vulnerability-uncovered-in-google-voice-browser-extension)]


Learn more [here](https://portswigger.net/daily-swig/xss).

## How to exploit it

We now know how this works, the risks, and some companies that were affected by it, how do we exploit it?

Calm your horses, trying XSS attacks is part of a PenTest work that’s subjected to a prior agreement with the owners of that software. If you’re interested in trying to exploit an application that doesn’t belong to you make sure you have a PenTest request signed first[2]. There are companies that have an active bug bounty program and if followed, you are allowed to test their systems.

Here are some lists of companies that you can try this on:

- Bugcrowd: [https://www.bugcrowd.com/bug-bounty-list/](https://www.bugcrowd.com/bug-bounty-list/)
- HackerOne: [https://hackerone.com/bug-bounty-programs](https://hackerone.com/bug-bounty-programs)
- Intigriti: [https://www.intigriti.com/programs](https://www.intigriti.com/programs)
- YesWeHack: [https://yeswehack.com/programs](https://yeswehack.com/programs)

## REMEMBER THAT TESTING LIVE SYSTEMS FOR VULNERABILITIES WITHOUT AUTHORIZATION IS A CRIME IN ALMOST EVERY COUNTRY

So let’s assume you are developing a web app and want to see if you’re vulnerable. The easiest way to do it is to run something link OWASP ZAP to crawl and test it for you.

![](/assets/img/post_images/OWASP-ZAP.png)

But if you want to test it manually you can go to any section that accepts user input and prints it back, like a comment section and you can try inserting a script tag with some javascript, just like in the next image.

![](/assets/img/post_images/Screenshot_2020-06-17_13-13-38.png)

**If you’re successful, you’ll see something like this:**

![](/assets/img/post_images/Screenshot_2020-06-17_13-14-00.png)


If not, maybe your application is already escaping some characters and if so we need to test evasion methods depending on where your input is being inserted, see a comprehensive list of evasion methods here: [https://owasp.org/www-community/xss-filter-evasion-cheatsheet](https://owasp.org/www-community/xss-filter-evasion-cheatsheet)

To exploit a reflected vulnerability we can search for places on our application where we print a message that is sent through a get parameter and test it using something like this:

[URL]/?error=\%3Cscript\%3Ealert\%281\%29\%3B\%3C\%2Fscript\%3E

This, if successful, will return the same result as the last attack.

Remember that it’s possible to escalate this vulnerability, depending on your application, but that will require you to use your imagination.

## As a developer, what can I do to protect myself against this?
A good place to start is to read these guidelines: [https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)

But I know that’s tedious for most developers, so the number one rule is to NEVER TRUST USER INPUT.

If you have user input and want to print it back on the webpage, always sanitize it (encode it and validate it) and whitelist some terms if needed only for example <br> or <p> tags.

Every web language already has some implementation of functions to help you in this, like htmlspecialchars and filter_input in PHP, and some frameworks like Django already escape what they can when printing variables, see [https://docs.djangoproject.com/en/3.0/topics/security/#cross-site-scripting-xss-protection](https://docs.djangoproject.com/en/3.0/topics/security/#cross-site-scripting-xss-protection)

## Bonus general security tips

- Be careful when clicking on weird links, it may be a Reflected XSS attack.
- Remember that every time you visit a website without TLS (HTTP instead of HTTPS) you are vulnerable to man-in-the-middle (MITM) attacks, and that in seconds a trained professional can have all that traffic intercepted, can add javascript to the pages you visit and of course, get your passwords.
- Check your email for known leaks related to your email addresses: [https://haveibeenpwned.com](https://haveibeenpwned.com)
- It’s safe to assume that if you reused the same combination of email/password in any other service those accounts are or will be compromised soon.
- Enable Two-factor authentication in every service that you can

[1] More about Cross-site script [https://www.precisesecurity.com/articles/](https://www.precisesecurity.com/articles/)

[2] [http://www.vulnerabilityassessment.co.uk/Presite%20Inspection.html](http://www.vulnerabilityassessment.co.uk/Presite%20Inspection.html)

