### Abstract
Fedaration is the future and the current implimentations are heavy, complicated, hard to understand, and genrally a pain in the neck to impliment, write programs for, and host. Mastodon sucks, its massive and eats up soooooo many resources for literally when you boil it down, something that transmits small peices of text. The rest of the Fediverse is basically all the same, shit, heavy, annoying, and looks bad.

This was originally an idea I had about building a fedarated text chat built around syncing text files, however it quickly expanded scope once I realized that I could sync directories, which can contain literally anything you want.

This document outlines how to impliment a full fedarated network where you can
 - watch videos
 - blog
 - tweet
 - chats (with text, images, videos, and links)
 - and even live steam
 
using nothing but unix tools (and stuff like lsyncd) and low cost low power servers.
For some small things we can use ssh, larger things we can use lsyncd, rsync, and possibly even DRBD.

### Core
- Every **object** (peice of media, chat, etc) is a **file**
- Every interaction is a **append** to a file
- Every **person** is a **user** on their home server
- Each **user** is addressed in their ssh connection name - ie.   user@server.com | user@123.12.345.123
- Each user has 3 folders 
    - **Public:** Tweets, blogs, videos, livesteams, etc.
        - Outward facing and can be read by anyone, these will appear in their public streams
    - **Private:** Group Text Chats, personal videos, etc.
        - Accessed by direct connections (eg. ssh) to the server only.
    - **Secret:** DM's, User follows, etc.
        - Accessed by direct connections (eg. ssh) to the server only
            - People can send files too it
            - **The name of the secret folder is your public key** (everything written to the secret folder should be encrypted)

### Notes
While this document outlines the methods one should impliment to be able to do all of these things, which is perfectly fine for power users, the ultamate goal is to make a user friendly GUI client for all of this, that is familiar and usable by people familiar with common services.
- **Videos** should feel similar to **Youtube**
- **Live streams** should feel similar to **Youtube**
- **Text**
    - posts under *280 characters* should feel similar to **Twitter**
    - posts over *280 characters* should feel like **Tumblr**
- **Chats**
    - **Group Chats** should have images, videos, and feel like **Discord/Telegram**
    - **Encrypted Group Chats** should be symmettrically encrypted and append only.
    - **Personal Chats** should be pub-priv key encrypted, secure, and feel like **Signal**
- **Voice and Video chats** should feel like Zoom
