I sometimes get confused between the different db rake tasks – what is the difference between ```db:setup``` and ```db:reset```, for example? So to clear up some of my confusion – and maybe some of yours – I have compiled this list of tasks with explanations.

* ```db:Creates``` - Creates the database for the current RAILS_ENV environment. If RAILS_ENV is not specified it defaults to the development and test databases.

* ```db:create:all``` - Creates the database for all environments.

* ```db:drop``` - Drops the database for the current RAILS_ENV environment. If RAILS_ENV is not specified it defaults to the development and test databases.

* ```db:drop:all``` - Drops the database for all environments.

* ```db:migrate``` - Runs migrations for the current environment that have not run yet. By default it will run migrations only in the development environment.

* ```db:migrate:redo``` - Runs db:migrate:down and db:migrate:up or db:migrate:rollback and db:migrate:migrate depending on the specified migration. I usually run this after creating and running a new migration to ensure the migration is reversable.

* ```db:migrate:up``` - Runs the up for the given migration VERSION.

* ```db:migrate:down``` - Runs the down for the given migration VERSION.

* ```db:migrate:status``` - Displays the current migration status.

* ```db:migrate:rollback``` - Rolls back the last migration.

* ```db:version``` - Prints the current schema version.

* ```db:forward``` - Pushes the schema to the next version.

* ```db:seed``` - Runs the db/seeds.rb file.

* ```db:schema:load``` - Loads the schema into the current environment’s database.

* ```db:schema:dump``` - Dumps the current environment’s schema to db/schema.rb.

* ```db:setup``` - Runs db:create, db:schema:load and db:seed.

* ```db:reset``` - Runs db:drop and db:setup.

* ```db:migrate:reset``` - Runs db:drop, db:create and db:migrate.

* ```db:test:prepare``` - Check for pending migrations and load the test schema. (If you run rake without any arguments it will do this by default.)

* ```db:test:clone``` - Recreate the test database from the current environment’s database schema.

* ```db:test:clone_structure``` - Similar to

* ```db:test:clone```, but it will ensure that your test database has the same structure, including charsets and collations, as your current environment’s database.

This was all taken from a combination of StackOverflow and the Rails source code.
