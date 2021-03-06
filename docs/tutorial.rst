********
Tutorial
********

.. toctree::
   :maxdepth: 2


Install
=======

You shouldn't have to do anything fancy. Just check out the code and run this
command from the project root ::

    pip install -r requirements.txt

Running
=======

From the project root, start the autologin service ::

    python service.py

Followed by ::

   scrapyd

Usage
=====

Here is an example of AutoLogin usage ::

   $ curl "http://localhost:5000/?seedurl=https://github.com/&username=actest1234&password=passpasspass123"


Note how we only specified the GitHub homepage. We don't need to specify the
actual login page, or any other information on the site: autologin will crawl
from the starting URL, find the login form, and submit authentication
credentials seamlessly.

The response looks like this ::

   {
      "redirected_to": "https://github.com/",
      "auth_headers":
      {
         "Accept-Language":
         [
            "en"
         ],

         "Accept-Encoding":
         [
            "gzip,deflate"
         ],

         "Accept":
         [
            "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8"
         ],

         "User-Agent":
         [
            "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:33.0) Gecko/20100101 Firefox/33.0"
         ],

         "Referer":
         [
            "https://github.com/login"
         ],

         "Cookie":
         [
            "_gh_sess=eyJsYXN0X3dyaXRlIjoxNDE2NDM3NzU1MTQ1LCJzZXNzaW9uX2lkIjoiZWI1YzJkYjE3YWFhNDQ4OWU1ZWZjN2Q5ZGFjZjRkZjIifQ%3D%3D--06456947bdba7a9b84b8a8938eb7086da99ef3f0; user_session=Xg9CSIRrxSCy2eZfv8_w4bJzd2iW9ZC5HG6oTIR8vhsSvNmNVG0f-0jGqnuQ4cgY58QGs_fnItf4Nnir; logged_in=yes; dotcom_user=actest1234"
         ]
      }
   }

If you then use the returned headers in your own tool, the website will think
you're authenticated – because you are! Enjoy!
