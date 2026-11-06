# Job Search HQ

Private dashboard for a UI/UX job search. This repo is only the website: a static `index.html` on GitHub Pages. No personal data lives here.

- **Data:** `data/jobs.json`, `data/network.json` and `data/settings.json` in the private repo `lamcrystal/job-search-hq-data`.
- **Access:** a fine-grained GitHub token (Contents read/write on the data repo only), entered once per device and kept in that browser's local storage. Without it the site shows a lock screen.
- **Background jobs:** Claude scheduled tasks read and write the data through `window.jobhq` on this page in Chrome. Nothing is ever sent automatically.

```js
await jobhq.ready
await jobhq.summary()
await jobhq.job(id)
await jobhq.update('jobs', d => { d[id].status = 'applied'; return d; }, 'commit message')
await jobhq.log('Scan: 4 new listings')
```
