---
creation date: Thursday 19th October 2023  9:25:46 am
modification date: Friday 12th September 2025  8:09:06 am
created by: Paul Miskovsky
tags: [note]
aliases: []
publish: true
title: Encrypt Files Using OpenSSL
---

# Encrypt Files Using OpenSSL

##### Here’s How to Encrypt a Single File Using a Password and a Salt:

```sh
openssl aes-256-cbc -salt -in filename -out filename.enc -base64
```

Type a strong password when prompted.

##### Here’s How to Decrypt the Same File:

```sh
openssl enc -d -aes-256-cbc -a -in filename.enc -out filename
```

You’ll need to re-enter the password that you used to encrypt it.

If you want to encrypt multiple files, combine them into a tar or zip archive before encrypting them.

You can replace `aes-256-cbc` with a different cipher if you prefer. You can get the list of available ciphers using `openssl -h`.

>[!caution]
>Once you’ve encrypted the file, immediately test that you can successfully decrypt it! You will be kicking yourself if you try to recover the data later on or send it to someone else and find that something is wrong with it.

---
tags: #note
links: [[Note Template]]
licence: [[Licences/CC BY-SA 4.0]]
code: [[Licences/GNU-GPL-v3.0]]
sources: 