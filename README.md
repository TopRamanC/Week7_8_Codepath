# Week7_8_Codepath
# Project 7 - WordPress Pentesting

Time spent: 16 hours spent in total

## Pentesting Report

### 1. WordPress <= 4.2 - Unauthenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: Cross-Site Scripting can be used when writing a comment in WordPress.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
  - [ ] GIF Walkthrough: 
  ![Exploit#1](https://user-images.githubusercontent.com/76242390/113984549-15513e80-9800-11eb-961b-e6cb021f9bf2.gif)

  - [ ] Steps to recreate: 
     1. Write and post a normal comment.
     2. Wrtie a comment with <a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>
     3. Make sure the size of the comment is bigger than 64kb.
     4. Log in as admin
     5. Approve and open the comment.
     6. Click "view page" and then a window will pop up saying "Hello".

### 2. Title: WordPress <= 4.2.3 - Nav Menu Title Cross-Site Scripting (XSS)
  - [ ] Summary: Cross-Site Scripting can be used when naming the title of a new page.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.4
  - [ ] GIF Walkthrough: 
  ![Exploit#2](https://user-images.githubusercontent.com/76242390/113984632-28640e80-9800-11eb-9cb9-1d7a756b9ec5.gif)
  - [ ] Steps to recreate: 
     1. Go to post tab to create a post
     2. Add any title and put the following script at the end of it: <script>alert(4)</script>
     3. Go to the main page and open your page and then 
a window will open saying "4"
 
### 3. Title: WordPress <= 4.2.2 - Authenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: Cross-Site Scripting can be used with the user who has posting access to post a page.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: 
  ![Exploit#3](https://user-images.githubusercontent.com/76242390/113986605-4763a000-9802-11eb-8a76-edb0fee1a326.gif)
  - [ ] Steps to recreate: 
    1. Make sure you are logged in as a user who can post a new page.
    2. In the description of the page post the following code <a href="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>
    3. Click on view page and a window will open saying "test".
