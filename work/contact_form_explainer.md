# How My Contact Form Works — Plain Words

## What's a Backend?

A backend is the part of a website that does something a plain page can't do.

A plain page just shows text and links. A backend remembers things — it takes a form submission, stores it, and emails me.

## What Does My Contact Form Do?

My contact form lets someone send me a message. They enter their name, email, and message, then click "Send." When they do, I get an email with their message.

## How Does the Data Flow?

Here's what happens step by step:

**Step 1:** Someone fills out the form on my site.

**Step 2:** When they click "Send," the form sends the data to Netlify's servers. Netlify is the service that hosts my site, and it has a built-in form handler.

**Step 3:** Netlify receives the data, checks that all required fields are filled, and stores the submission.

**Step 4:** Netlify sends an email to my inbox with the message details: name, email, and what they wrote.

**Step 5:** I see the email and reply directly.

## Why This Is a "Backend" (Even Though I Didn't Build a Server)

Netlify is doing the backend work for me:
- It receives the form data
- It stores it
- It emails me

I didn't have to build a server. I just added a few attributes to my form, and Netlify handles the rest.

---

**Live URL:** https://breattah.netlify.app
