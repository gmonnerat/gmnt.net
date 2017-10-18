+++
title = "How to Rename an App in Django(Part 2)"
date = 2017-10-18T17:03:02-02:00
description = "Automate the migration in production"
keywords = ["python3", "python", "django"]
categories = ["python", "django"]
+++

After rename an app and play a bit with [Django migrations](https://docs.djangoproject.com/en/1.11/topics/migrations/) based on the link posted [here](https://www.gmnt.net/post/how-to-rename-an-app-in-django/), I noticed that `manage.py migrate` was not moving the data to new table in my test environment.

To test massively, I used the backup and the script below to simulate the migration.

```
cat <<PGSCRIPT | sudo -u postgres psql
/* drop database from my test environment */
DROP DATABASE $DATABASE;
/* create the database from scratch*/
CREATE DATABASE $DATABASE with encoding = "utf-8";
PGSCRIPT

/* restore the database from backup */
gunzip -c $DATABASE.dump.gz | sudo -u postgres psql $DATABASE
/* run django migrations */
manage.py migrate

cat <<PGSCRIPT | sudo -u postgres psql $DATABASE
/* copy everything */
INSERT INTO new_table_address (SELECT * from old_table_address);
/* increase sequence, otherwise it fails to create a new object */
SELECT setval('new_table_address_id_seq', nextval('old_table_address_id_seq'));

INSERT INTO new_table_patient (SELECT * from old_table_patient);
SELECT setval('new_table_patient_id_seq', nextval('old_table_patient_id_seq'));
PGSCRIPT
```

In production, I only do :

```
/* run django migrations */
manage.py migrate

cat <<PGSCRIPT | sudo -u postgres psql $DATABASE

/* copy everything */
INSERT INTO new_table_address (SELECT * from old_table_address);
/* increase sequence, otherwise it fails to create a new object */
SELECT setval('new_table_address_id_seq', nextval('old_table_address_id_seq'));

INSERT INTO new_table_patient (SELECT * from old_table_patient);
SELECT setval('new_table_patient_id_seq', nextval('old_table_patient_id_seq'));
PGSCRIPT
```


