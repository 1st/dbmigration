DB migration toolkit with YAML syntax
===========

**Under development.** You can help me speedup this process.

```yaml
# migrations/migraton_2013-04-30.yaml
migrations:
 - create_table:
   name: comments
   comment: Store comments
   columns:
     id: {type: INTEGER, auto_increment: true, pk: true}
     user_id: {type: INTEGER, not_null: true}
     title: {type: VARCHAR(70)}
     text: {type: TEXT}
- change_table:
  - name: comments
  - add_fk: {from: comments.user_id, to: users.id}
  - rename_column: {from: id, to: comment_id}
```
