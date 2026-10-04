# vendor/

Third-party readers used by resume import to read PDF and Word files **on the
person's own device**. They are served from this site, not from another host,
and they load only when someone picks a PDF or Word file.

| File | What it is | Version | Licence |
|---|---|---|---|
| `pdf.min.js` | pdf.js, Mozilla's PDF reader (legacy build, for older phones) | 5.6.205 | Apache-2.0 |
| `pdf.worker.min.js` | pdf.js background worker (same version) | 5.6.205 | Apache-2.0 |
| `jszip.min.js` | JSZip, opens .docx files (a .docx is a zip) | 3.10.1 | MIT |

The pdf.js files are the unmodified `legacy/build/pdf.min.mjs` and
`legacy/build/pdf.worker.min.mjs` from the `pdfjs-dist` npm package, renamed to
`.js` so every web server sends a JavaScript content type. JSZip is the
unmodified `dist/jszip.min.js` from the `jszip` npm package.

SHA-256, to confirm the files have not been altered:

```
0d29c4871eff0b72f3896825f2673ddf7dfbccf815a7095a5d14f5aa68fab0e5  pdf.min.js
7fc442c268d107d656755252cf38c422a88e825b7f0caaac6a5f58364dff4179  pdf.worker.min.js
acc7e41455a80765b5fd9c7ee1b8078a6d160bbbca455aeae854de65c947d59e  jszip.min.js
```

Why these live here and not on a public code host: this site keeps people's
sign-in sessions in the browser, so any script it runs can reach them. Serving
the readers ourselves means no outside host can change what runs.

To update: replace all three files together, update the versions and hashes
above, and re-run the page tests against the new files.
