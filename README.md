# Server database setup

The car API reads its MySQL connection from `DB_HOST`, `DB_PORT`, `DB_USER`, `DB_PASSWORD`, and `DB_NAME`.

1. Copy `.env.example` to `.env` and set a valid database user and password. Do not commit `.env`.
2. Restore the SQL exports only into an empty database. From Command Prompt in this directory, run the commands below, entering the database password when prompted:

   ```cmd
   mysql --host=student-databases.cvode4s4cwrc.us-west-2.rds.amazonaws.com --user=your_mysql_user -p HUNTERANDERSON753 < sql/car_attributes.sql
   mysql --host=student-databases.cvode4s4cwrc.us-west-2.rds.amazonaws.com --user=your_mysql_user -p HUNTERANDERSON753 < sql/car_selection.sql
   ```

   Create the empty database first if it does not exist. Import `car_attributes.sql` first because `car_selection.sql` has a foreign key to it. These exports create tables and insert rows, so importing them into populated tables will fail.
3. Start the API from this directory with `npm start`. This uses Node.js 20.6 or newer.

The dump targets the database named `HUNTERANDERSON753`. If the database host or name changes, update both the import commands and `.env` to match.