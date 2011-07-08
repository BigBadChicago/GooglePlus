The Google+ API
===

Below is documentation on how to access Google+ resources. It's based on the access patterns of the
browser.

1 Authentication
===

Authentication is performed by simply POSTing your credentials to a service and tracking cookies. To
kick it off, grab some cookies from:

1.1 GET http://plus.google.com
---

We do this just to collect some cookies.

1.2 GET https://www.google.com/accounts/ServiceLogin?service=oz&continue=https://plus.google.com/?gpcaz%3DXXXXXXXX&ltmpl=es2st&hideNewAccountLink=1&hl=en-US
---

We need some more cookies; specifically, **GALX** which gets set thanks to this call. You will need
to substitute **gpcaz** with the one you got from 1.1.

1.3 POST https://www.google.com/accounts/ServiceLoginAuth
---

We pass our credentials to this service to authenticate.

    Content-Type	application/x-www-form-urlencoded

    ltmpl		es2st
    pstMsg		1
    dnConn		https://accounts.youtube.com
    continue	https://plus.google.com/?gpcaz=XXXXXXXX
    service		oz
    hl			en-US
    timeStmp	
    secTok	
    GALX		# From cookies in 1.2
    Email		# Email address
    Passwd		# Password
    PersistentCookie	yes
    rmShown		1
    signIn		Sign in
    asts

On a successful POST, you will get back the G+ home page. That page contains a lot of
JavaScript data in `<script>` tags. The next section covers some of that data.

2 The API Data
===

TBD
