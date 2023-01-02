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



### Set up db
https://flask.palletsprojects.com/en/2.2.x/tutorial/database/

Using sqlite for the sake of being easy.

```from flask import g, current_app```
g - special object unique to each request; store current db in here
current_app - special object that points to the Flask application itself; this allows us to act like it's a global even though we have defined an app factory.

Question: Why do the `from . import db` import inline within `flaskr/__init__.create_app`?
 * perhaps this let's us use the imported g/current_app properly?
