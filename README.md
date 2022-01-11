# smtp-mail-server-django

 
**Installation Steps:-**
Install virtualenv: `sudo pip install virtualenv`

Create a new virtual environment to run your django setup: `virtualenv env`

Activate the virtual environment : `source env/bin/activate`

Install the requirements for the virtual environment: `pip install -r requirements.txt`

**Now:-**
`send_mail`(_subject_,  _message_,  _from_email_,  _recipient_list_,  _fail_silently=False_,  _auth_user=None_,  _auth_password=None_,  _connection=None_,  _html_message=None_)[[source]](https://docs.djangoproject.com/en/1.8/_modules/django/core/mail/#send_mail)[¶](https://docs.djangoproject.com/en/1.8/topics/email/#django.core.mail.send_mail "Permalink to this definition")

The simplest way to send email is using  `django.core.mail.send_mail()`.

The  `subject`,  `message`,  `from_email`  and  `recipient_list`  parameters are required.

-   `subject`: A string.
-   `message`: A string.
-   `from_email`: A string.
-   `recipient_list`: A list of strings, each an email address. Each member of  `recipient_list`  will see the other recipients in the “To:” field of the email message.
-   `fail_silently`: A boolean. If it’s  `False`,  `send_mail`  will raise an  [`smtplib.SMTPException`](https://docs.python.org/3/library/smtplib.html#smtplib.SMTPException "(in Python v3.8)"). See the  [`smtplib`](https://docs.python.org/3/library/smtplib.html#module-smtplib "(in Python v3.8)")  docs for a list of possible exceptions, all of which are subclasses of  [`SMTPException`](https://docs.python.org/3/library/smtplib.html#smtplib.SMTPException "(in Python v3.8)").
-   `auth_user`: The optional username to use to authenticate to the SMTP server. If this isn’t provided, Django will use the value of the  [`EMAIL_HOST_USER`](https://docs.djangoproject.com/en/1.8/ref/settings/#std:setting-EMAIL_HOST_USER)  setting.
-   `auth_password`: The optional password to use to authenticate to the SMTP server. If this isn’t provided, Django will use the value of the  [`EMAIL_HOST_PASSWORD`](https://docs.djangoproject.com/en/1.8/ref/settings/#std:setting-EMAIL_HOST_PASSWORD)  setting.
-   `connection`: The optional email backend to use to send the mail. If unspecified, an instance of the default backend will be used. See the documentation on  [Email backends](https://docs.djangoproject.com/en/1.8/topics/email/#topic-email-backends)  for more details.
-   `html_message`: If  `html_message`  is provided, the resulting email will be a  _multipart/alternative_  email with  `message`  as the  _text/plain_  content type and  `html_message`  as the  _text/html_  content type.

The return value will be the number of successfully delivered messages (which can be  `0`  or  `1`  since it can only send one message).

## Lets Send Some Mail;
To start the shell: ``python manage.py shell``

This will create a shell with all the Django settings already configured for us. Inside that brand new shell, paste the following code:
```python
>>> from django.core.mail import send_mail
>>> from django.conf import settings
```
```python
>>> send_mail('A cool subject', 'A stunning message', settings.EMAIL_HOST_USER, ['email1@gmail.com','email2@gmail.com','email3@gmail.com'])
```

Let’s break down the code above:

-   We import the Django  [send_mail](https://docs.djangoproject.com/en/3.2/topics/email/#send-mail)  function.
-   Then we import the  `settings`  object which contains all the  [global settings](https://github.com/django/django/blob/main/django/conf/global_settings.py)  and the per-site settings (those inside the  `settings.py`  file).
-   Finally, we pass all the needed arguments to the  `send_mail`  function. This function returns the number of emails sent, in this case,  **1**.
