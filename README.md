# nuxt-hydration-bug

## Reproduce procedure

1. Generate static assets and start server
   ```
   npm install
   npm run generate
   npm run start
   ```
2. Visit root page, expect no error, pass
   ```
   http://localhost:3000
   ```
3. Click first link (id0) from root page, expect no error, pass
   ```
   http://localhost:3000/%E3%84%A9%E3%84%87/id0/
   ```
4. Reload id0 page by pressing F5 or browser reload button, expect no error in console, failed
   ```
   http://localhost:3000/%E3%84%A9%E3%84%87/id0/
   ```

## Observation

When there is non ascii code in url, such as `ㄩㄇ` in this example, payload won't load.

All javascript, except the one triggered from `layout/` directly, are not executed.

For example, please edit content in the input box at bottom of `id0` page, although there's a `v-model`, the data attributes is not reactive.
