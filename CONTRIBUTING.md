# Contributing

TODO: The code is not quite ready yet for anyone to contribute. `deploy.ts` must
be abstracted into separate utilities that can be independently run to avoid the
final deploy step.

To get started, clone the repo, run `npm i`, and then `npm run build` (or `npm
run watch`). We use TypeScript, so code must be compiled before it runs.

## Process

Starters are generated by overlaying starter files (located in
`<type>/starters/<name>`) onto base files (located in `<type>/base/`) in a
temporary directory.

Then, if a starter manifest file is found (located at
`<type>/starters/<name>.json`), additional operations on the generated starter
files occur. For example, if the `dependencies` key is found in the manifest
file, it will merge those dependencies into `package.json` before the archive
process.

Finally, an archive of the generated starter files is created and gzipped and
uploaded to an S3 bucket. The S3 bucket has a CloudFront distribution for
close-proximity downloads. The distribution ID is `E1XZ2T0DZXJ521` and can be
found [at this URL](https://d2ql0qc7j8u4b2.cloudfront.net).

## Deploying

Starters are deployed automatically when new commits are pushed to the `master`
branch. To deploy manually, run:

`npm run deploy`