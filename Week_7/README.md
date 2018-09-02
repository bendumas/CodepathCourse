# Project 7 - WordPress Pentesting

Time spent: **8** hours spent in total

> Objective: Find, analyze, recreate, and document **three vulnerabilities** affecting an old version of WordPress

## Pentesting Report

NOTE: Below, there will be instances of |<| and |>|. The vertical bars should not be there during the exploit.

1. (Required) Unauthenticated Genericons Cross-Site Scripting
  - [X] Summary: 
    - Vulnerability types: Cross-Site Scripting
    - Tested in version: 4.1
    - Fixed in version: 4.2.2
  - [X] GIF Walkthrough:
      ![Alt text](/Exploit1.gif?raw=true "Exploit 1")
  - [X] Steps to recreate: 
    1. Ensure that WordPress version 4.1 is running.
    2. Navigate to http://wpdistillery.dev/wp-content/themes/twentyfifteen/genericons/example.html
    3. Add "#1|<|img src=1 onerror=alert(1)|>|" to the end of the URL
    4. Complete! See https://wpvulndb.com/vulnerabilities/7979 for information.
  - [X] Affected source code:
    - [Link 1] https://core.trac.wordpress.org/browser/tags/version/src/wp-content/themes/twentyfifteen/genericons/example.html
    
    
2. (Required) Large File Upload Error XSS (CVE-2017-9061)
  - [X] Summary: 
    - Vulnerability types: Cross-Site Scripting
    - Tested in version: 4.1
    - Fixed in version: 4.7.5
  - [X] GIF Walkthrough: 
      ![Alt text](/Exploit2.gif?raw=true "Exploit 2")
  - [X] Steps to recreate: 
    1. Ensure that WordPress version 4.1 is running. 
    2. Create a large (20 MB) file named "Dinosaurs secret life|<|img src=x onerror=alert(1)|>|.png" for example. 
      - This was the example file name given in the writeup. It could be anything. The key is to notice that an image tag can be embedded. 
      - I created a large file using -- # fallocate -l 20M "Dinosaurs secret life|<|img src=x onerror=alert(1)|>|.png"
    3. Navigate to http://wpdistillery.dev/wp-admin/media-new.php
    4. Upload the file you just created.
    5. Complete! See https://hackerone.com/reports/203515 for information
  - [X] Affected source code:
    - [Link 1] https://core.trac.wordpress.org/browser/tags/version/src/wp-content/themes/twentyfifteen/genericons/media-new.php
    
    
3. (Required) Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds (CWE 79)
  - [X] Summary: 
    - Vulnerability types: Cross-Site Scripting
    - Tested in version: 4.6
    - Fixed in version: 4.7.2
  - [X] GIF Walkthrough: 
      ![Alt text](/Exploit3.gif?raw=true "Exploit 3")
  - [X] Steps to recreate: 
    1. Ensure that WordPress version 4.6 is running. 
    2. A contributor to the site creates a post with a very specific format.
      - " [embed src='https://youtube.com/embed/12345\x3csvg onload=alert(1)\x3e'][/embed] " without the quotes on either side is what I used
      - The full reasoning for this choice is in the walkthrough below.
    3. The contributor submits the post for review.
    4. The admin reviews the post. 
    5. Complete! See https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html for the full walkthrough.
  - [X] Affected source code:
    - [Link 1] https://core.trac.wordpress.org/browser/tags/version/src/wp-includes/embed.php

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

I had trouble identifying an exploit for a certain vulnerability. Many times, a vulnerability would be very 
loosely described, and it would be the reader's responsibility to craft this into an exploit. This wouldn't
be an issue if I were familiar with WordPress, but I am not. Therefore, I spent a lot of time finding out
what I could and could not do with WordPress. 

## License

    Copyright 2017 Benjamin Dumas

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
