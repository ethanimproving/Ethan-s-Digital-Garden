# Digital Obsidian Garden
This is the template to be used together with the [Digital Garden Obsidian Plugin](https://github.com/oleeskild/Obsidian-Digital-Garden). 
See the README in the plugin repo for information on how to set it up.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/oleeskild/digitalgarden)

---
## Docs
Docs are available at [dg-docs.ole.dev](https://dg-docs.ole.dev/)

# Changes to default

## Support Jul 8, 2005 Date Format

In `timestamps.njk` make the following change:

```javascript
// This supports ISO standard format
el.innerHTML = luxon.DateTime.fromISO(el.getAttribute('data-date') || el.innerText).toFormat(TIMESTAMP_FORMAT);
// This supports the evernote format such as: Jan 16, 2023, 11:51 AM
el.innerHTML = luxon.DateTime.fromFormat(el.getAttribute('data-date') || el.innerText, 'MMM d, yyyy, h:mm a').toFormat(TIMESTAMP_FORMAT);
```
