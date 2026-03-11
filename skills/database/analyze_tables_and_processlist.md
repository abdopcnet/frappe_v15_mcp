If migrate blocks: check processlist, KILL blocking connection, then re-run migrate.

```python
# In MariaDB: SHOW PROCESSLIST; then KILL <id>;
# Or use bench/scripts to find and kill blocker.
```
