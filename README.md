DB migration toolkit with YAML syntax
===========

**Under development.** You can help me speedup this process.

It's written on Python.

```yaml
# migrations/migraton_2013-04-30.yaml
migrations:

- create_table__comments:
   comment: Store comments
   columns:
     id: {type: INTEGER, auto_increment: true, pk: true}
     user_id: {type: INTEGER, not_null: true}
     name: {type: VARCHAR(70)}
     text: {type: TEXT}
     notes: {type: TEXT}
     date_create: {type: DATETIME}

- change_table__comments:
   - add_fk: {from: user_id, to: users.id}
   - create_column: {name: is_approved, type: BOOLEAN, default: FALSE}
   - rename_column: {from: id, to: comment_id}
   - rename_column: {from: name, to: title}
   - delete_column: notes
   - delete_column: date_create
   # or builk operations
   - create_columns:
     - {name: is_approved, type: BOOLEAN, default: FALSE}
     - {name: is_hidden, type: BOOLEAN, default: FALSE}
   - rename_columns:
     - {from: id, to: comment_id}
     - {from: name, to: title}
   - delete_columns:
     - notes
     - date_create

 # advanced option, not recommended!
 - raw_sql: ALTER TABLE `comments` ADD COLUMN `followers` (INTEGER)
```
