## Following Flask Tutorial
https://flask.palletsprojects.com/en/2.2.x/tutorial/


### conda setup
```
$ conda create -n flaskr
$ conda activate flaskr
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
