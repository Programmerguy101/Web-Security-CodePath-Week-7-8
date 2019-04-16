# Web-Security-CodePath-Week-7-8

## Penetrationing Test Report


1. (Required) DOM Cross-Site Scripting (XSS) via Post
  - [x] Summary: A user can post a script as normal post and run a script once the post is published. 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Theme: Twenty Fifteen
    - Tested in Version: 1.1
    - Fixed in version: 1.2
  - [x] GIF Walkthrough: ![](Wordpress-1.gif)
  - [x] Steps to recreate: 
  1. Insert this line of code into the post:
  ```
  http:// site.com/wp-content/themes/twentyfifteen/genericons/example.html#1<img/ src=1 onerror= alert(1)>
  ```
  
  2. On the preview, we can see that the script is being ran. 
  
  - [x] Affected source code:
    - [Link 1](https://blog.sucuri.net/2015/05/jetpack-and-twentyfifteen-vulnerable-to-dom-based-xss.html)

2. (Required) Cross-Site Scripting (XSS) via Image Title
  - [x] Summary: A user can change the title of an image and attach it to a post in order to run a script once the image is clicked on. 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 
  - [x] GIF Walkthrough: ![](Wordpress-2.gif)
  - [x] Steps to recreate: 
  1. Insert this line of code into the picture's title:
  ```
  cengizhansahinsumofpwn<img src=a onerror=alert(document.cookie)>.jpg
  ```
  2. Create a new post and add a gallery including that picture.
  3. On the preview, we can see that the script is being ran. 
  
  - [x] Affected source code:
    - [Link 1](https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_vulnerability_in_wordpress_due_to_unsafe_processing_of_file_names.html)
3. (Required) Stored Cross-Site Scripting
  - [x] Summary: A user with editing privileges can inject a script in a reply message which is executed when the mouse is hovered over the link.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
  - [x] GIF Walkthrough: ![](Wordpress-3.gif)
  - [x] Steps to recreate:
  1. Using an account with editing privileges, make a reply with the following text:
  ```
  <a href = "" onmouseover=alert("Hi") >Click here</a>
  ```
  2. Once someone hovers there mouse over the link, the script will be ran.
  - [x] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/4.2/src/wp-includes/comment-template.php)
4. (Optional) Cross-Site Scripting (XSS) via Media File Metadata
  - [x] Summary: A user can upload an audio file with meta data containing a script to be exectued once the audio file is added to a post's playlist
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.13
  - [x] GIF Walkthrough: ![](Wordpress-4.gif)
  - [x] Steps to recreate:
  1. Download the xss.mp3 audio file found at the bottom of this page: https://seclists.org/oss-sec/2017/q1/563
  Any audio file should work as long as its meta data is properly formatted to run the specified script.
  2. Create a new post and add the audio file to the post's playlist
  
  - [x] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/28f838ca3ee205b6f39cd2bf23eb4e5f52796bd7)
5. (Optional) User Enumeration
  - [x] Summary: Wordpress informs you when the username doesn't exist or when it does exist but got the wrong password. Hackers can guess a username and then just have to brute force the password to gain access to that account. 
    - Vulnerability types: User Enumeration
    - Tested in version: 4.2
    - Fixed in version: This was never fixed. Wordpress doesn't se this as a vulnerability. Other websites are similar where usernames are visible. In previous labs we had to guess an accounts username before moving forward which now makes me think that it as risky if usernames are public. 
  - [x] GIF Walkthrough: ![](Wordpress-5.gif)
  - [x] Steps to recreate: 
  1. Entering in a username that doesn't exist informs us there's no account with that username.
  2. Entering in a username but the wrong password, informs us the password is wrong but we can infer that an account with that username does exist. 
  - [x] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/4.2/src/wp-includes/user.php)
    
    
## Assets

Utilized WPScan to find vulnarebilities in old version of wordpress

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)


## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2019] [Owen Ahmed]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
