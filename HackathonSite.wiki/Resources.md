#### Fetch an icon from a given query
**Possible query parameters**
- `color`: `black`, `white`, `red` (default: `black`)
- `format`: `svg`, `png` (default: `png`)
- `size`: `16`, `24`, `32`, `48`, `64`, `128`, `256`, `512` (default: `48`)
- `name`: any of the FA icon names ([look here](https://fortawesome.github.io/Font-Awesome/icons/)) (default: `file`)

Example:
```javascript
GET /resources/icon?color=red&format=png&size=128&name=calendar

HTTP/1.1 200 OK
// An icon of the requested type
```