## Run CRM on the built-in server

!!! Note
    Don't use this server in anything resembling a production environment (with access to the CRM from the Internet).  
    It is intended only for use on a personal computer or in intranet - a private local network (for example, during development).

``` cmd
python manage.py runserver
```

In this case, [Django CRM](https://docs.djangoproject.com/en/dev/ref/contrib/admin/){target="_blank"} will be available only on your computer on the IP address `http://127.0.0.1:8000` (localhost with port 8000).  
Open the web page at this address in your browser.  
If you need to provide access to CRM from an intranet (local network), specify the IP address of your network card and port  

!!! Important
    But first, [specify the CRM website domain](#specify-crm-site-domain).

For example:

```cmd
python manage.py runserver 1.2.3.4:8000
```

## Access to CRM and admin sites

Now you have two websites.  
Use the superuser credentials to log in.  

CRM site for all users:  
`http://127.0.0.1:8000/en/123/`  
It's according to the template  
`<your CRM host>/<LANGUAGE_CODE>/<SECRET_CRM_PREFIX>`

and Admin site for administrators (superusers):  
`http://127.0.0.1:8000/en/456-admin`  
`<your CRM host>/<LANGUAGE_CODE>/<SECRET_ADMIN_PREFIX>`

`LANGUAGE_CODE`, `SECRET_CRM_PREFIX` and `SECRET_ADMIN_PREFIX`
can be changed in the file `webcrm/settings.py`

!!! Note 
    Do not attempt to access the bare `<your CRM host>` address ( `http://127.0.0.1:8000/` ).  
    This address is not supported.  
    To protect CRM with a site server (e.g. [Apache](https://httpd.apache.org/){target="_blank"}), a redirect to a fake login page can be placed on this address.

## Specify CRM site domain

By default, CRM software is configured to work on a domain "localhost" (ip: 127.0.0.1).  
To work on another domain (or IP address), you need to do the following:  

- In the SITES section for administrators (superusers):  
`(ADMIN site) Home > Sites > Sites`  
Add a CRM site and specify its domain name.
- In the file `webcrm/settings.py`:
  - specify its id in the setting `SITE_ID`,
  - add it to the setting `ALLOWED_HOSTS`.


## Built-in assistance system

Many pages have an icon <span style="vertical-align: baseline"><img src="../icons/question-mark.svg" alt="Question-mark icon" width="25" height="25"></span> in the upper right corner.  
This is a link to a help page.

Many buttons and icons on CRM pages have tooltips that appear when you hover your mouse over them.
