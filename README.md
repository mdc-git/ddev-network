# ddev-network

## Auto add all ddev projects as external links

**Note: This will not install if `jq` is not found in your `PATH`**. https://stedolan.github.io/jq/download/
## Example

```sh
user@host:~$ ddev list
┌──────────────────┬─────────┬────────────────────────────────────┬───────────────────────────────┬───────────┐
│ NAME             │ STATUS  │ LOCATION                  │ URL                           │ TYPE      │
├──────────────────┼─────────┼────────────────────────────────────┼───────────────────────────────┼───────────┤
│ project1         │ OK      │ /PATH/TO/project1         │ https://project1.ddev.site    │ php       │
├──────────────────┼─────────┼────────────────────────────────────┼───────────────────────────────┼───────────┤
│ project2         │ stopped │ /PATH/TO/project2         │ https://project2.ddev.site    │ php       │
├──────────────────┼─────────┼────────────────────────────────────┼───────────────────────────────┼───────────┤
│ project3         │ stopped │ /PATH/TO/project3         │ https://project3.ddev.site    │ php       │
├──────────────────┼─────────┼────────────────────────────────────┼───────────────────────────────┼───────────┤
│ project4         │ stopped │ /PATH/TO/project4         │ https://project4.ddev.site    │ php       │
├──────────────────┼─────────┼────────────────────────────────────┼───────────────────────────────┼───────────┤
│ project5         │ stopped │ /PATH/TO/project5         │ https://project5.ddev.site    │ php       │
├──────────────────┼─────────┼────────────────────────────────────┼───────────────────────────────┼───────────┤
│ project6         │ stopped │ /PATH/TO/project6         │ https://project6.ddev.site    │ php       │
├──────────────────┼─────────┼────────────────────────────────────┼───────────────────────────────┼───────────┤
│ project7         │ stopped │ /PATH/TO/project7         │ https://project7.ddev.site    │ php       │
├──────────────────┼─────────┼────────────────────────────────────┼───────────────────────────────┼───────────┤
│ Router           │ stopped │ ~/.ddev                            │                               │ original: │
│                  │         │                                    │                               │  v1.21.4  │
└──────────────────┴─────────┴────────────────────────────────────┴───────────────────────────────┴───────────┘
```

will create a file `.ddev/docker-compose.network.yaml` with the following content assuming you run it in `project1` :

```yaml
# Map any external links to the router here.
services:
  web:
    external_links:
      - 'ddev-router:project2.ddev.site'
      - 'ddev-router:project3.ddev.site'
      - 'ddev-router:project4.ddev.site'
      - 'ddev-router:project5.ddev.site'
      - 'ddev-router:project6.ddev.site'
      - 'ddev-router:project7.ddev.site'
```

## Usage

```
ddev get mdc-git/ddev-network
ddev restart
```
