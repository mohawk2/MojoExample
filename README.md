<img src="https://cloud.githubusercontent.com/assets/63439/3788824/8ef74550-1a7a-11e4-9313-4a4009bc859a.png" />

# Purpose of this GraphQL-orientated fork

To demonstrate GraphQL on Mojolicious working with a DBIx::Class database.
Follow the GraphiQL link and try this query:

```
{
  blog(id: [1, 2]) {
    id
    title
    tags {
      name
    }
  }
}
```

# Purpose

- [Introduction](http://tempi.re/mojolicious-full-and-lite-apps-understanding-the-difference)
- Compare a [full Mojolicious app](https://github.com/tempire/MojoExample/) to a [lite app](https://github.com/tempire/MojoExample/blob/master/mojolite) with the same functionality.
- See an example of DBIx::Class usage with Mojolicious
- See an example of tests for a Mojolicious app

## Notes

- Both apps make use of the DBIx::Class schema.
- The schema is in lib/Schema.pm, lib/Schema/*
- The DBIx::Class schema connects to a provided sqlite3 database, test.db
- The controller tests create a new test.db, populated using fixtures from t/fixtures/*
- The schema tests use an in-memory sqlite3 database, populated using fixtures
  from t/fixtures/*
- Test::Database is a utility for populating the sqlite3 databases with
  fixtures from t/fixtures/*


# Usage

## Live

<a href="http://mojoexample.herokuapp.com/">Running on Heroku</a>

Heroku is running Hypnotoad, the *full featured UNIX optimized preforking 
non-blocking I/O HTTP 1.1 and WebSocket server built around the very well 
tested and reliable Mojo::Server::Daemon with IPv6, TLS, Bonjour, libev 
and hot deployment support that just works*.

To easily deploy your own Mojolicious app to Heroku, check out <a href="http://tempire.github.com/mojolicious-command-deploy-heroku">Deploy Perl Mojolicious web apps to Heroku</a>.

## Locally

A minimum of Perl 5.10 is required.  If your Perl is too old, <a href="http://perlbrew.pl/">Perlbrew</a> is über easy to install!

If you *must* run on Perl 5.8, you can try a <a href="https://github.com/jamadam/mojo-legacy">back-ported version of Mojolicious</a>, but you're on your own :)

### Install

	git clone git@github.com:tempire/MojoExample.git
	cd MojoExample


Install the Carton package manager. Carton will install all dependencies
to the local/ sub-directory.

	curl -L cpanmin.us | perl - Carton
	carton install

### Run

#### Full app

	carton exec morbo script/mojo_full

#### Light app

	carton exec morbo mojolite

# Index

* [lib/](https://github.com/tempire/MojoExample/blob/master/lib)
    * [MojoFull.pm](https://github.com/tempire/MojoExample/blob/master/lib/MojoFull.pm)       - Mojolicious Application
    * [MojoFull/](https://github.com/tempire/MojoExample/blob/master/lib/MojoFull)         - Mojolicious Controllers
        * [Blogs.pm](https://github.com/tempire/MojoExample/blob/master/lib/MojoFull/Blogs.pm)
        * [Home.pm](https://github.com/tempire/MojoExample/blob/master/lib/MojoFull/Home.pm)
        * [Photos.pm](https://github.com/tempire/MojoExample/blob/master/lib/MojoFull/Photos.pm)
    * [Schema.pm](https://github.com/tempire/MojoExample/blob/master/lib/Schema.pm)         - DBIx::Class model 
    * [Schema/](https://github.com/tempire/MojoExample/blob/master/lib/Schema)
        * [Result/](https://github.com/tempire/MojoExample/blob/master/lib/Schema/Result)         - DBIx::Class Result classes
            * [Blog.pm](https://github.com/tempire/MojoExample/blob/master/lib/Schema/Result/Blog.pm)
            * [BlogTag.pm](https://github.com/tempire/MojoExample/blob/master/lib/Schema/Result/BlogTag.pm)
            * [Photo.pm](https://github.com/tempire/MojoExample/blob/master/lib/Schema/Result/Photo.pm)
            * [Photoset.pm](https://github.com/tempire/MojoExample/blob/master/lib/Schema/Result/Photoset.pm)
        * [ResultSet/](https://github.com/tempire/MojoExample/blob/master/lib/Schema/ResultSet/)      - DBIx::Class ResultSet classes
            * [Blog.pm](https://github.com/tempire/MojoExample/blob/master/lib/Schema/ResultSet/Blog.pm)
            * [Photo.pm](https://github.com/tempire/MojoExample/blob/master/lib/Schema/ResultSet/Photo.pm)
            * [Photoset.pm](https://github.com/tempire/MojoExample/blob/master/lib/Schema/ResultSet/Photoset.pm)
    * [Test/](https://github.com/tempire/MojoExample/blob/master/lib/Test/)
        * [Database.pm](https://github.com/tempire/MojoExample/blob/master/lib/Test/Database.pm)     - Utility class for populating test fixtures
* [public/](https://github.com/tempire/MojoExample/blob/master/public/)             - Static files
    * [css/](https://github.com/tempire/MojoExample/blob/master/public/css/)
        * [main.css](https://github.com/tempire/MojoExample/blob/master/public/css/main.css)
    * [images/](https://github.com/tempire/MojoExample/blob/master/public/images/)
        * [background.gif](https://github.com/tempire/MojoExample/blob/master/public/images/background.gif)
        * [bender_promo.png](https://github.com/tempire/MojoExample/blob/master/public/images/bender_promo.png)
        * [box-bottom.png](https://github.com/tempire/MojoExample/blob/master/public/images/box-bottom.png)
        * [box-middle.gif](https://github.com/tempire/MojoExample/blob/master/public/images/box-middle.gif)
        * [box-top.png](https://github.com/tempire/MojoExample/blob/master/public/images/box-top.png)
        * [profile_top.png](https://github.com/tempire/MojoExample/blob/master/public/images/profile_top.png)
    * [script/](https://github.com/tempire/MojoExample/blob/master/script/)             - Utilities
        * [generate_schema](https://github.com/tempire/MojoExample/blob/master/script/generate_schema)   - Generates DBIx::Class schema from database file
        * [mojo_full*](https://github.com/tempire/MojoExample/blob/master/script/mojo_full)
        * [new_db](https://github.com/tempire/MojoExample/blob/master/script/new_db)            - Generates database file from DBIx::Class and fixtures
* [t/](https://github.com/tempire/MojoExample/blob/master/t/)                  - Tests
    * [fixtures/](https://github.com/tempire/MojoExample/blob/master/t/fixtures/)         - Fixtures (placeholder data) for tests
        * [Blog.pl](https://github.com/tempire/MojoExample/blob/master/t/fixtures/Blog.pl)
        * [Photoset.pl](https://github.com/tempire/MojoExample/blob/master/t/fixtures/Photoset.pl)
    * [schema/](https://github.com/tempire/MojoExample/blob/master/t/schema/)           - DBIx::Class model tests
        * [blog.t](https://github.com/tempire/MojoExample/blob/master/t/schema/blog.t)
        * [blog_tag.t](https://github.com/tempire/MojoExample/blob/master/t/schema/blog_tag.t)
        * [photo.t](https://github.com/tempire/MojoExample/blob/master/t/schema/photo.t)
        * [photoset.t](https://github.com/tempire/MojoExample/blob/master/t/schema/photoset.t)
    * [home.t](https://github.com/tempire/MojoExample/blob/master/t/home.t)            - Home.pm controller tests
    * [blogs.t](https://github.com/tempire/MojoExample/blob/master/t/blogs.t)           - Blogs.pm controller tests
    * [photos.t](https://github.com/tempire/MojoExample/blob/master/t/photos.t)          - Photos.pm controller tests
* [templates/](https://github.com/tempire/MojoExample/blob/master/templates/)
    * [blogs/](https://github.com/tempire/MojoExample/blob/master/templates/blogs/) - Blogs.pm templates
        * [index.html.ep](https://github.com/tempire/MojoExample/blob/master/templates/blogs/index.html.ep) - Tag Helpers
        * [show.html.ep](https://github.com/tempire/MojoExample/blob/master/templates/blogs/show.html.ep)
    * [home/](https://github.com/tempire/MojoExample/blob/master/templates/home/) - Home.pm templates
        * [index.html.ep](https://github.com/tempire/MojoExample/blob/master/templates/home/index.html.ep)
    * [photos/](https://github.com/tempire/MojoExample/blob/master/templates/photos/) - Photos.pm templates
        * [index.html.ep](https://github.com/tempire/MojoExample/blob/master/templates/photos/index.html.ep)
        * [show.html.ep](https://github.com/tempire/MojoExample/blob/master/templates/photos/show.html.ep)
        * [show_set.html.ep](https://github.com/tempire/MojoExample/blob/master/templates/photos/show_set.html.ep)
    * [layouts/](https://github.com/tempire/MojoExample/blob/master/templates/layouts/)
        * [default.html.ep](https://github.com/tempire/MojoExample/blob/master/templates/layouts/default.html.ep)
* *[mojolite](https://github.com/tempire/MojoExample/blob/master/mojolite)* - Mojolicious::Lite app, with all the application files listed above embedded
* [README.md](https://github.com/tempire/MojoExample/blob/master/README.md)           - This file

# Copyright License

Copyright (C) 2008-2014, Glen Hinkle.

MojoExample is free software, you can redistribute it and/or modify it under the same terms as Perl5 (http://dev.perl.org/licenses/).
