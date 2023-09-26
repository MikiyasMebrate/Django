# How to Send Email in Django Using Gmail

If you're building a Django project and need to send emails, you can use the built-in `send_mail()` function and configure your settings to use Gmail as your email backend. In this tutorial, we'll show you how to send a test email using Django and Gmail.

### Prerequisites

Before we get started, you'll need to have the following:

- A Gmail account
- A Django project set up on your computer
- Basic knowledge of Django

### Configuring Email Settings

To configure your email settings in Django, open up your `settings.py` file and add the following code:

```
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = 'user@gmail.com'
EMAIL_HOST_PASSWORD =''

```

Replace `user@gmail.com` with your actual Gmail address, and enter your Gmail password in the `EMAIL_HOST_PASSWORD` field.

### Sending a Test Email

Now that your email settings are configured, you can use the `send_mail()` function to send a test email. Add the following code to your Django project:

```
from django.core.mail import send_mail

send_mail(
    "Django",
    "Test From Django Project.",
    "mikiyasmebrate2656@gmail.com",
    ["relotiw465@mevori.com","lcxz4s@wuuvo.com"],
    fail_silently=False,
)

```

This will send an email with the subject "Django" and the message "Test From Django Project." to the email addresses specified in the `recipient_list` argument.

### Conclusion

In this tutorial, we showed you how to send email in Django using Gmail. With this knowledge, you can now send emails from your Django project using Gmail as your email backend.