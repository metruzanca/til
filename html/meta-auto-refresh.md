# How to Auto Refresh an HTML page

Apprently theres a meta tag that auto refreshes your page:
```html
<meta http-equiv="refresh" content="30" >
```
In this case this will auto refresh the page every 30 seconds. Useful for if you're designing a very simple dashboard thats meant to be on display data but isn't going to be interracted with very often or can't e.g. a TV on the wall of an office. Great if you don't want/need to implement complicated logic to update the data.
