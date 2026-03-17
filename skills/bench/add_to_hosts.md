# Add To Hosts

Use this when a local development site needs hostname mapping.

## Example

```bash
echo "127.0.0.1 site.local" | sudo tee -a /etc/hosts
```

## Note

This is an OS step, not a Frappe database action.
