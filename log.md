## Following Flask Tutorial
https://flask.palletsprojects.com/en/2.2.x/tutorial/


### venv setup
```
$ python3 -m venv venv
$ . venv/bin/activate
```



<details>
  <summary> Project Layout</summary>

  https://flask.palletsprojects.com/en/2.2.x/tutorial/layout/


  General Theory:
  ```/home/user/Projects/flask-tutorial
  ├── flaskr/
  │   ├── __init__.py
  │   ├── db.py
  │   ├── schema.sql
  │   ├── auth.py
  │   ├── blog.py
  │   ├── templates/
  │   │   ├── base.html
  │   │   ├── auth/
  │   │   │   ├── login.html
  │   │   │   └── register.html
  │   │   └── blog/
  │   │       ├── create.html
  │   │       ├── index.html
  │   │       └── update.html
  │   └── static/
  │       └── style.css
  ├── tests/
  │   ├── conftest.py
  │   ├── data.sql
  │   ├── test_factory.py
  │   ├── test_db.py
  │   ├── test_auth.py
  │   └── test_blog.py
  ├── venv/
  ├── setup.py
  └── MANIFEST.in
  ```

</details>

### Set up application factory
https://flask.palletsprojects.com/en/2.2.x/tutorial/factory/

* Why do this in the `__init__.py` file? (vs importing this func)
  * `__init__.py` let's python know that the surrounding directory is a package

Reading https://hackersandslackers.com/flask-application-factory/ to answer a bit of the "why" question below.

Interesting: https://stackoverflow.com/questions/128478/should-import-statements-always-be-at-the-top-of-a-module
* could be ```In the __init__.py of a plugin, which might be imported but not actually used. Examples are Bazaar plugins, which use bzrlib's lazy-loading framework.```


### Set up db
https://flask.palletsprojects.com/en/2.2.x/tutorial/database/

Using sqlite for the sake of being easy.

```from flask import g, current_app```
g - special object unique to each request; store current db in here
current_app - special object that points to the Flask application itself; this allows us to act like it's a global even though we have defined an app factory.

Question: Why do the `from . import db` import inline within `flaskr/__init__.create_app`?
 * perhaps this let's us use the imported g/current_app properly?


### Blueprints and Views

Spent some time to better understand functools and decorators in general.
https://docs.python.org/3/library/functools.html
https://realpython.com/primer-on-python-decorators/

also found potential answer to why we are importing inline.


### Templates & Static files
https://flask.palletsprojects.com/en/2.2.x/tutorial/templates/
https://flask.palletsprojects.com/en/2.2.x/tutorial/static/

Basically seems to use Jinja2 for templates, and function `render_from_template` will look in the `app/templates/...` directory to find appropriate files.
Static files are served similarly automagically if they are placed in `app/static`.


### Blog Blueprint

Basic implementation of a blog by reading and writing from our DB once we are logged in.
I like the @login_required wrapper.

Missing a way to look at all items from a single user say -- this is a weird shared blog I suppose / vs a blog platform.

I still feel like I don't understand general GET/POST/PUT etc... theory, not sure what to do about that though.
i.e. in this context it's fairly clear what's happening, I suppose the form submit stuff is a little confusing to me...
When you click submit it simply posts to this same address with form data attached I guess.
