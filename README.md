### Abstract
This was originally an idea I had about building a fedarated text chat built around syncing text files, however it quickly expanded scope once I realized that I could sync directories, which can contain literally anything you want.

This document outlines how to impliment a full fedarated network where you can
 - watch videos
 - blog
 - tweet
 - chats (with text, images, videos, and links)
 - and even live steam
 
 using nothing but unix tools (and stuff like lsyncd) and low cost low power servers.
 For some small things we can use ssh, larger things we can use lsyncd, rsync, and possibly even DRBD.

### Core Prinipals
- Every object (peice of media, chat, etc) is a file
- Every interaction is a stream
- Every person is a user on their home server
- There's a public folder, private folder, and a secret folder
    - Public: Tweets, blogs, videos, livesteams, etc.
        - Outward facing and can be read by anyone, these will appear in their public streams
    - Private: Text chats, personal videos, etc.
        - Accessed by direct connections (eg. ssh) to the server only.
    - Secret: DM's, etc.
        - Accessed by direct connections (eg. ssh) to the server only, write only you cant read.
