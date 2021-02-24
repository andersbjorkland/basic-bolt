Bolt 4 standard project skeleton
================================

Welcome! This is a Bolt 4 project, set up using `composer create-project`. If
you are the developer of this project, you can modify this README to the
specifics of your project. Below are the general instructions to set up a _new_
project, based off the same skeleton.


Note: If you're updating from an earlier beta, read UPDATE.md for details.

---

Set up a new Bolt 4 project, using the following command, replacing
`myprojectname` with your desired project's name.

```bash
composer create-project bolt/project myprojectname
```

Navigate into the newly created folder, and configure the database in `.env`.
You can skip this step, if you'd like to use SQLite.

```dotenv
# SQLite
DATABASE_URL=sqlite:///%kernel.project_dir%/var/data/bolt.sqlite

# MySQL
DATABASE_URL=mysql://root:"root%1"@127.0.0.1:3306/four
```

Set up the database, create the first user and add fixtures (dummy content):

```bash
bin/console bolt:setup
```

Run Bolt using the built-in webserver, Symfony CLI, Docker or your own
preferred webserver:

```bash
bin/console server:start
```

or…

```bash
symfony server:start -d
symfony open:local
```

or…

```bash
make docker-install
```

Finally, open the new installation in a browser. If you've used one of the
commands above, you'll find the frontpage at http://127.0.0.1:8000/ \
The Bolt admin panel can be found at http://127.0.0.1:8000/bolt

Log in using the credentials you created when setting up the first user.

## Contributing

If you'd like to contribute, please check [Bolt's core repository](https://github.com/bolt/core/blob/master/CONTRIBUTING.md) 
and read the ["Contributing to Bolt"](https://docs.bolt.cm/4.0/other/contributing) documentation page.

## Deploying
### Shared hosting
When on shared hosting you most often will have to change how your project is structured. 
The content of your project's public folder will need to be placed on the shared host's designated 
public folder, e.g. www_public or public_html or similar. 
 
You will also have to change (or add) a key value pair in **compose.json** so that the key extra.public-dir points to the public-path.
```
{
    "...": "...",
    "extra": {
        "...": "...",
        "public-dir": "my_new_public_dir"
    }
}
```

In the official docs from Symfony: ["Override the Public Directory"](https://symfony.com/doc/current/configuration/override_dir_structure.html#override-the-public-directory)
