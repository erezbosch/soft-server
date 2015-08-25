## Rails-style web server program
### Features
* Model classes which inherit from the SQLObject class can have associations and
are searchable &mdash; the `where` function is lazily evaluated and stackable.
* Controller classes have access to `params` hash and `session`/`flash` cookies.
* Controller classes have working `redirect_to` methods.
* Controller classes have working `render` methods which render ERB templates.
* Router's `draw` method will create routes as specified.
* `protect_from_forgery` and `form_authenticity_token` methods can be used to
authenticate users.

### How to Use
* Write a .sql file containing the details of your database.
* Change the values of the DB_FILE and SQL_FILE constants in
`db_logic/db_connection` to reflect the name of your .sql file.
* Write model classes that inherit from SQLObject (you'll have to `require` or
`require_relative` `db_logic/sql_object`). You can write associations as in
Rails, just call `finalize!` at the end of the class definition.
* Write controller classes that inherit from ControllerBase (you'll have to
`require` or `require_relative` `controller_logic/controller_base` as well as
the appropriate model class).
* Write a script that creates a router with the appropriate routes and requires
your model and controller files, then starts up a WEBRick server. An example is `bin/integration_test_server.rb`.
* Write `.html.erb` templates in a `views` folder as appropriate.
* If you write a form, make sure to provide a `form_authenticity_token`.

### File organization
#### bin
* scripts to run test servers

#### controller_logic
* ControllerBase class
* Classes ControllerBase uses (Flash, Params, Route, Router, Session)

#### db_logic
* SQLObject and database access classes (ActiveRecord Lite)

#### controllers, models, views
* Files for the integration example
