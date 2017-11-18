# FlaskBase
## Base structure for a flask project with a little magic.

This is a blueprint for every small-to-medium flask + SQLAlchemy projects. Designed to be cloned and used on the fly.

## Basic usage

Use git to clone this repo, rename/reset the local clone and start building your project.
```shell
git clone https://github.com/Hrabal/FlaskBase.git
```
If you want to later host your project on GitHub or similar, mirror this repo:

```shell
git clone --bare https://github.com/Hrabal/FlaskBase.git

mv FlaskBase.git YourProjectName.git
cd YourProjectName.git
git push --mirror https://github.com/YourGitHubUser/YourProjectRepository.git
```

Edit the `config.py` file to change the db settings (default is a SqlLite db named after the directory your project is in).

Site routes and URIs should be defined in the views directory, avery SQLAlchemy models file should be placed in the models subdirectory.

The static folder is divided into `css`, `files`, `img` and `js` sobfolders, store your static resources here.

## Db commodities

Db migration scripts are based (well... stolen) from the great [Miguel Grinberg's The Flask Mega-Tutorial](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iv-database), read it to understand what's happening.

For a quick start run the scripts:

```shell
python3 db_create.py
python3 db_migrate.py
python3 db_upgrade.py
```
## Views magic

Every `.py` file in the views directory will be loaded and **executed**. That means that every `@app.route` registered in the views directory will be served.
