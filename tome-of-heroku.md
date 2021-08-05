# Tome of Heroku

## Deploying an existing Rails app on Heroku

1. If your Rails app is still using the default SQLite3 database, you must migrate to someting like PostgreSQL.
1.1 Install PostgreSQL
```bash
$ brew install postgresql
$ brew services start postgresql
```

1.1 Create database user for your app

1.2 Replace the sqlite3 gem with pg gem. Open your `Gemfile` and replace the line:
`gem sqlite3`
with:
`gem pg`
Then install the gem:
`$ bundle install`

1.3 Replace your database adapter. Open your `config/database.yml` file. Replace the line `adapter: sqlite3` with `adapter: postgresql`. You can get a sample of a complete PostgreSQL `config/database.yml` file on the [Heroku DevCenter](https://devcenter.heroku.com/articles/getting-started-with-rails6#add-the-pg-gem).

2. Install the Heroku command-line interface (CLI). This is available via [Homebrew](https://www.brew.sh). A detailed walkthrough can be found again on the [Heroku DevCenter](https://devcenter.heroku.com/articles/heroku-cli#download-and-install).

```bash
$ brew tap heroku/brew && brew install heroku install heroku-cli
```

3. Update gems for Linux platform, if necessary. For those developing on macOS (and likely other operating systems), the gems specified in `Gemfile` and `Gemfile.lock` may have different versions depending on the platform. That is, there maybe different releases of a gem for Linux, Mac, etc... Since Heroku hosts on Linux devices, it is important for your `Gemfile.lock` to identify the correct gem for the correct platform.

```bash
$ bundle lock --add-platform x86_64-linux
```

4. Test your build for production deployment. This is a good tip to validate your app builds correctly for the production release. I ran into one situation where, for whatever reason, the app would crash on start during production deployment but the exact same app launched perfectly fine on development mode on my local machine. 

```bash
$ RAILS_ENV=production rails server
```

5. Deploy to Heroku. NOTE make sure all your changes have been merged to the `main` branch prior to deploying.

```bash
$ git heroku push main
```

6. Migrate your database on Heroku

```bash
$ heroku run rake db:migrate
```
