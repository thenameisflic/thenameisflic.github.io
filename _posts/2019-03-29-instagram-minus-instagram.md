---
layout: single
title: "Instagram minus Instagram"
header:
  image: https://pics.thenameisflic.com/media/images/anon/best-buddies-trying-out-pics-Z3IA4P.jpg
---

TL;DR: I created an Instagram bot account that posts my pics from my website with all faces censored. Continue reading to know why and how.

It's no secret [i don't like social media](https://thenameisflic.com/why-i-dont-use-social-media). However, i have to give them credit where credit is due: they are unparalleled in their ease of use and their potential to keep us in touch with our closest friends. Taking these benefits into account, i created [Flic Pics](pics.thenameisflic.com), a simple way to use and share my own personal pics.

What it does right now:
- Upload pics through Telegram, my instant messenger of choice
- Creates two versions of the pic: one with a watermark and one with all  faces censored.
- With an account, you can view the watermarked, uncensored version. (I need to create an account for you, just [text me on Telegram](https://t.me/flicsl))
- The censored version gets posted to Instagram's Stories in my [bot account](https://instagram.com/thenameisflicbot).

> I want to censor faces so that Instagram and other bad actors don't use them to, you know, track me and my friends around.

# The tech

It uses Django for all of the web goodiness, Bootstrap because its Bootstrap. The fun parts are the glue that bring all of that together.

### Creating a Telegram bot

Telegram bots are stupidly easy to create with [python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot). I have no idea how (and don't have the time right now to look into it), but you don't even need to host the code in some VPS to start hacking: it lets you do all on localhost. You just need to configure a bot in 30 seconds using the [Botfather on Telegram](https://t.me/botfather), get the access token and use it with the library to start responding to commands (or, in my case, photos).

### Censoring faces

I used [face_recognition](https://github.com/ageitgey/face_recognition) for its sheer ease of use. Just take a look at everything you need to find all faces in a picture:

```python
import face_recognition
image = face_recognition.load_image_file("your_file.jpg")
face_locations = face_recognition.face_locations(image)
```

However, in my tests so far, it hasn't been very accurate. In [slightly tilted faces](https://pics.thenameisflic.com/media/images/auth/file_19jpg-R41M0O.jpg) it doesn't seem to work at all. I understand that might be just because i'm using the faster version (because i'm cheap and can't afford a VPS with a GPU).

### Uploading to Instagram

This was the biggest surprise to me: it's super easy to do this with [Instagram-API-python](https://github.com/LevPasha/Instagram-API-python)! Look at the example code:

```python
from InstagramAPI import InstagramAPI

InstagramAPI = InstagramAPI("login", "password")
InstagramAPI.login()  # login

photo_path = '/path/to/photo.jpg'
caption = "Sample photo"
InstagramAPI.uploadPhoto(photo_path, caption=caption)
```

All libraries should expose an interface like that (on second thought, i wouldn't have a job if they did). Amazingly, it worked at first try and so far i haven't been rate limited even when i was debugging. There's a caveat, though: if you need to post stories, try [using my fork](https://github.com/thenameisflic/Instagram-API-python/), since the original one doesn't support posting stories.

---

That's all, folks! If you want, you can follow my bot account on [Instagram](https://instagram.com/thenameisflicbot), or check the [source on Github](https://github.com/thenameisflic/pics). In the future, i fully intend to make it available as a service, since perhaps there are other people who could find this useful as well.

Thank you so much for reading!
